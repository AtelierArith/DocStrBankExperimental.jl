```
set_normalized_rhs(
    constraints::AbstractVector{<:ConstraintRef},
    values::AbstractVector{<:Number}
)
```

Set the right-hand side terms of all `constraints` to `values`.

Note that prior to this step, JuMP will aggregate all constant terms onto the right-hand side of the constraint. For example, given a constraint `2x + 1 <= 2`, `set_normalized_rhs([con], [4])` will create the constraint `2x <= 4`, not `2x + 1 <= 4`.

## Example

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, con1, 2x + 1 <= 2)
con1 : 2 x ≤ 1

julia> @constraint(model, con2, 3x + 2 <= 4)
con2 : 3 x ≤ 2

julia> set_normalized_rhs([con1, con2], [4, 5])

julia> con1
con1 : 2 x ≤ 4

julia> con2
con2 : 3 x ≤ 5
```
