```
MissingPackage(pkg::Base.PkgId)
```

The package `pkg` was asked for, but does not seem to be available in the current environment.

# Example occurrence

```julia-repl
julia> @addpkg Bar "00000000-0000-0000-0000-000000000000"
Bar [00000000-0000-0000-0000-000000000000]

julia> @import Bar
[ Info: Lazy-loading Bar [00000000-0000-0000-0000-000000000001]
ERROR: MissingPackage: Bar [00000000-0000-0000-0000-000000000001] has been required, but does not seem to be installed.
Stacktrace: [...]
```
