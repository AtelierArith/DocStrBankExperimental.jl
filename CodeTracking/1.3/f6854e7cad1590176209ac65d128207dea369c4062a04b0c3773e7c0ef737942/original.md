```
sigs = signatures_at(mod::Module, relativepath, line)
```

For a package that defines module `mod`, return the signatures of all methods whose definition spans the specified location. `relativepath` indicates the path of the file relative to the packages top-level directory, e.g., `"src/utils.jl"`. `line` must correspond to a line in the method body (not the signature or final `end`).

Returns `nothing` if there are no methods at that location.
