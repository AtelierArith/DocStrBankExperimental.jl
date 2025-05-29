```
get_concrete_platform(platform::AbstractPlatform;
                      preferred_gcc_version = nothing,
                      preferred_llvm_version = nothing,
                      compilers = nothing)
```

Return the concrete platform for the given `platform` based on the GCC compiler ABI.  The set of shards is chosen by the keyword arguments (see [`choose_shards`](@ref)).
