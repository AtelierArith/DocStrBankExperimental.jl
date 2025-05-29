```
reduced_cost(x::VariableRef)::Float64
```

Return the reduced cost associated with variable `x`.

Equivalent to querying the shadow price of the active variable bound (if one exists and is active).

See also: [`shadow_price`](@ref).
