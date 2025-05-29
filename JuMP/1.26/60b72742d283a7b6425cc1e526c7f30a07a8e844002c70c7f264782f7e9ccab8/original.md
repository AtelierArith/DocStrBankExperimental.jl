```
normalized_rhs(constraint::ConstraintRef)
```

Return the right-hand side term of `constraint` after JuMP has converted the constraint into its normalized form.

See also [`set_normalized_rhs`](@ref).

## Example

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, con, 2x + 1 <= 2)
con : 2 x ≤ 1

julia> normalized_rhs(con)
1.0
```
