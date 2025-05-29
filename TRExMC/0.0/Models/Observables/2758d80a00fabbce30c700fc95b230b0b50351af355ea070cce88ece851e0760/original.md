```
@observables name symbol_funcs::AbstractDict
@observables name symbols funcs
```

Generate an [`AbstractObservables`](@ref) subtype with the given `name` whose fields will be denoted by the given `symbols` iterable. The [`measure!`](@ref) method will also be implemented with the supplied [`funcs`] iterable.

Alternatively one can supply a `Dict`ionary of symbol-function pairs as a single argument.

!!! note
    `length(symbols) == length(funcs)` by construction.

