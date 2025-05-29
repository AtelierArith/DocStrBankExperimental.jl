```
@cpimport module depot_path::AbstractString
```

Import `module` using `depot_path` to store and retrieve the precompile cache. Precompile caches existing elsewhere are ignored.

The semantics of `@cpimport` probably differ from those of `import` in other ways.

# Examples:

Import the module `Example` using "./newdepot" for storing and retrieving the precompile cache.

```
julia> @cpimport Example "./newdepot"
```
