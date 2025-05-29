```
normalized_coefficient(
    constraint::ConstraintRef,
    variable::GenericVariableRef,
)
```

Return the coefficient associated with `variable` in `constraint` after JuMP has normalized the constraint into its standard form.

See also [`set_normalized_coefficient`](@ref).

## Example

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, con, 2x + 3x <= 2)
con : 5 x ≤ 2

julia> normalized_coefficient(con, x)
5.0

julia> @constraint(model, con_vec, [x, 2x + 1, 3] >= 0)
con_vec : [x, 2 x + 1, 3] ∈ Nonnegatives()

julia> normalized_coefficient(con_vec, x)
2-element Vector{Tuple{Int64, Float64}}:
 (1, 1.0)
 (2, 2.0)
```
