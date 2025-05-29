```
UnregisteredPackage(pkg::Symbol, mod::Module)
```

The package `pkg` was asked for within `mod`, but has not been registered by `mod`, and so cannot be loaded.

# Example occurrence

```julia-repl
julia> @import Foo
ERROR: UnregisteredPackage: Foo has not been registered by Main, see @addpkg for more information
Stacktrace: [...]
```
