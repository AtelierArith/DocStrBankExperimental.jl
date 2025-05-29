```
BuildDependency(dep::Union{PackageSpec,String}; platforms)
```

Define a binary dependency that is necessary only to build the package.  The `dep` argument can be either a string with the name of the JLL package or a `Pkg.PackageSpec`.

The optional keyword argument `platforms` is a vector of `AbstractPlatform`s which indicates for which platforms the dependency should be used.  By default `platforms=[AnyPlatform()]`, to mean that the dependency is compatible with all platforms.
