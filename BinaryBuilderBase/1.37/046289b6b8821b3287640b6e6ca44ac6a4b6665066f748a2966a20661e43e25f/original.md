```
RuntimeDependency(dep::Union{PackageSpec,String}; compat::String, platforms::Vector{<:AbstractPlatform}, top_level::Bool=false)
```

Define a binary dependency that is only listed as dependency of the generated JLL package, but its artifact is not installed in the prefix during the build.  The `dep` argument can be either a string with the name of the JLL package or a `Pkg.PackageSpec`.

The optional keyword argument `compat` can be used to specify a string for use in the `Project.toml` of the generated Julia package.

The optional keyword argument `platforms` is a vector of `AbstractPlatform`s which indicates for which platforms the dependency should be used.  By default `platforms=[AnyPlatform()]`, to mean that the dependency is compatible with all platforms.

The optional keyword argument `top_level` specifies whether the dependency should be use only at the top-level of the generated JLL package, instead of inside each platform-specific wrapper.  Using `top_level=true` is useful for packages needed for platform augmentation (e.g. `MPIPreferences.jl`).
