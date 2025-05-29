```
AbstractAlgebra.add_verbosity_scope(s::Symbol) -> Nothing
```

Add the symbol `s` to the list of (global) verbosity scopes. For use inside a module this function must be called in the  `__init__` function of that module; the verbosity scope is then available to all functions in the module.

# Examples

```jldoctest
julia> AbstractAlgebra.add_verbosity_scope(:MyScope)

```
