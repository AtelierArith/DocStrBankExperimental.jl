```
generate_compiler_wrappers!(platform::AbstractPlatform; bin_path::AbstractString,
                            host_platform::AbstractPlatform = Platform("x86_64", "linux"; libc = "musl", cxxstring_abi = "cxx11"),
                            compilers::Vector{Symbol} = [:c],
                            allow_unsafe_flags::Bool = false,
                            lock_microarchitecture::Bool = true,
                            gcc_version::Union{Nothing,VersionNumber}=nothing,
                            clang_version::Union{Nothing,VersionNumber}=nothing,
                            clang_use_lld::Bool = false,
                            )
```

We generate a set of compiler wrapper scripts within our build environment to force all build systems to honor the necessary sets of compiler flags to build for our systems. Note that while `platform_envs()` sets many environment variables, those values are intended to be optional/overridable.  These values, while still overridable by directly invoking a compiler binary directly (e.g. /opt/{target}/bin/{target}-gcc), are much more difficult to override, as the flags embedded in these wrappers are absolutely necessary, and even simple programs will not compile without them.
