```
parameter_refs(vref::InfiniteVariableRef)::Tuple
```

Return the parameter references associated with the infinite variable `vref`. This is formatted as a Tuple of containing the parameter references as they inputted to define `vref`.

**Example**

```julia-repl
julia> @variable(model, T, Infinite(t))
T(t)

julia> parameter_refs(T)
(t,)
```
