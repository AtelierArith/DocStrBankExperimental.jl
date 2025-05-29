```
infinite_variable_ref(vref::PointVariableRef)::GeneralVariableRef
```

Return the `InfiniteVariableRef` associated with the point variable `vref`.

**Example**

```julia-repl
julia> @variable(model, T, Infinite(t))
T(t)

julia> @variable(model, T0, Point(T, 0))
T0

julia> infinite_variable_ref(T0)
T(t)
```
