```
parameter_refs(vref::SemiInfiniteVariableRef)::Tuple
```

Return the infinite parameter references associated with the semi-infinite variable `vref`. This is formatted as a `Tuple` of containing the parameter references as they were inputted to define the untranscripted infinite variable except, the evaluated parameters are excluded.

**Example**

```julia-repl
julia> parameter_refs(vref)
(t, [x[1], x[2]])
```
