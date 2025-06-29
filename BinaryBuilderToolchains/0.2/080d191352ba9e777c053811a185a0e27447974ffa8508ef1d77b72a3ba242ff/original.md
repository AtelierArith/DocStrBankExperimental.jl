```
AbstractToolchain
```

An `AbstractToolchain` represents a set of JLLs that should be downloaded to provide some kind of build capability; an example of which is the C toolchain which is used in almost every recipe, but fortran, go, rust, etc.. are all other toolchains which can be included in the build environment.

All toolchains must define the following methods:

  * Constructor

      * used to configure tool versions, etc...
  * toolchain_sources(toolchain)

      * returns a vector of `AbstractSource`'s representing the dependencies needed to run this toolchain, relative to some installation prefix
  * toolchain*env(toolchain, deployed*prefix::String)

      * returns a dictionary listing the environment variables to be added in to commands that use this toolchain.
  * platform(toolchain)

      * returns the platform this toolchain was constructed for.  Could be a `CrossPlatform` (in the case of CToolchain) or a plain `Platform` (in the case of HostToolsToolchain).
  * supported_platforms(::Type{toolchain})

      * returns a list of platforms (with no tags) that this toolchain supports targeting.
