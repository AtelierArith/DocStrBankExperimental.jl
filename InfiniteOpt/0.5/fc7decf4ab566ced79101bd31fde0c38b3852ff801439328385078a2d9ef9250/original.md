```
parameter_values(vref::PointVariableRef)::Tuple
```

Return the support point associated with the point variable `vref`.

**Example**

```julia-repl
julia> @variable(model, T, Infinite(t))
T(t)

julia> @variable(model, T0, Point(T, 0))
T0

julia> parameter_values(T0)
(0,)
```
