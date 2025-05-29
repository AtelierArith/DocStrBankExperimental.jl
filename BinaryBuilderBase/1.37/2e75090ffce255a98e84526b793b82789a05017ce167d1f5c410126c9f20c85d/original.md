```
gcc_version(p::AbstractPlatform, GCC_builds::Vector{GCCBuild},
            compilers::Vector{Symbol}=[:c];
            llvm_version::Union{Nothing,VersionNumber}=nothing)
```

Returns the closest matching GCC version number for the given particular platform, from the given set of options.  The compiler ABI and the microarchitecture of the platform will be taken into account.  If no match is found, returns an empty list.  `compilers` is the list of compilers used in the build, to choose the right version of GCC to couple with them if necessary.  If the keyword argument `llvm_version` is passed, it is used to filter the version of GCC for FreeBSD platforms.

This method assumes that the compiler ABI of the platform represents a platform that binaries will be run on, and thus versions are always rounded down; e.g. if the platform supports a `libstdc++` version that corresponds to `GCC 5.1.0`, but the only GCC versions available to be picked from are `4.8.5` and `5.2.0`, it will return `4.8.5`, as binaries compiled with that version will run on this platform, whereas binaries compiled with `5.2.0` may not.
