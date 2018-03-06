
# JVM FastText

This project is an attempt to compile Facebook's Fast Text (written in c++) for the JVM

## Project Layout

The project follows the standard Maven layout:

```
src/main/c     -- C++ Sources
src/test/java  -- Java test sources demonstrating how the C files can be used (well, once it's working
pom.xml        -- Maven setup
```

## Requirements

The GCC-Bridge maven plugin requires GCC 4.7 to be installed to compile C++ and Fortran Sources. 

You will also need Java 1.8 and Apache Maven 3.x.

On Ubuntu 14.04, you can install all required tools via `apt-get`:

```
sudo apt-get install maven gcc-4.7 gcc-4.7-plugin-dev gfortran-4.7 gcc-4.7.multilib
```

I suggest grabbing the vagrant file from the main renjin repository and using that to avoid any issues.

## Compiling

You can build the java library by running

```
mvn install
```

## Challenges

The following challenges were encountered:
 * Figuring out how to get the maven plugin to see the .cc sources (renamed to .cpp, but this should be fixed in a new plugin release)
 * Figuring out how to set the compiler flags (refered to an example + looked at the plugin source)
 * GCC would crash - I've commented out the calls that trigger a crash... but that's not a real long-term solution
    * calls to std::make_shared
    * calls to push_back on std::vector instances
    * calls to push on std::priority_queue instances



 


