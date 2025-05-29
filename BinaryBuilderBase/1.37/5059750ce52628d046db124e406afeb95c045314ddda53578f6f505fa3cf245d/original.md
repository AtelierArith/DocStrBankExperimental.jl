```
Dependency(dep::Union{PackageSpec,String}, build_version::VersionNumber;
           compat::String, platforms::Vector{<:AbstractPlatform})
```

Define a binary dependency that is necessary to build the package and load the generated JLL package.  The argument can be either a string with the name of the JLL package or a `Pkg.PackageSpec`.

The optional positional argument `build_version` can be used to specify the version of the dependency to be installed when building it.  If not specified, the latest version of the package compatible with the environment will be automatically chosen by the package resolver, unless `compat` is specified, see below.

The optional keyword argument `compat` can be used to specify a string for use in the `Project.toml` of the generated Julia package.  If `compat` is non-empty and `build_version` is not passed, the latter defaults to the minimum version compatible with the `compat` specifier.

The optional keyword argument `platforms` is a vector of `AbstractPlatform`s which indicates for which platforms the dependency should be used.  By default `platforms=[AnyPlatform()]`, to mean that the dependency is compatible with all platforms.

The optional keyword argument `top_level` denotates that this dependency is platform independent. It implies that the `platforms` keyword argument is set to `[AnyPlatform()]`. The primary use-case is for packages that hold information about the platform selection using `Preferences`. Platform selection is cached and in the case that no platform is available we need to be able to invalidate said cache. Invalidation occurs through the package that owns the `Preferences` data.
