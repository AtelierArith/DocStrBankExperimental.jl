```
infinite_variable_ref(vref::SemiInfiniteVariableRef)::GeneralVariableRef
```

Return the infinite variable/derivative/parameter function reference associated  with the semi-infinite variable `vref`.

**Example**

```julia-repl
julia> infinite_variable_ref(vref)
g(t, x)
```
