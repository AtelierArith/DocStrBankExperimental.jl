```
add_complex_vector_of_phase_variable!
```

Add a complex variable to the model `m` indexed by

1. `var_symbol` like `:v`
2. `bus_or_edge`
3. `time_step`  # TODO have not made the swap of time and bus*or*edge in this method yet
4. phase in `[1, 2, 3]`

```julia
# initialize variable as zeros that will remain for undefined phases

m[var_symbol][bus_or_edge][time_step] = convert(
    Vector{GenericAffExpr{ComplexF64, VariableRef}}, 
    [0im; 0im; 0im]
)
```

Upper and lower bounds are added if provided using constraints.
