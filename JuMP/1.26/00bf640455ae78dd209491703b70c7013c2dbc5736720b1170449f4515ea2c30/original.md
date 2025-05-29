```
set_normalized_coefficient(
    constraints::AbstractVector{<:ConstraintRef},
    variables_1:AbstractVector{<:GenericVariableRef},
    variables_2:AbstractVector{<:GenericVariableRef},
    values::AbstractVector{<:Number},
)
```

Set multiple quadratic coefficients associated with `variables_1` and `variables_2` in the constraints `constraints` to `values`.

Note that prior to this step, JuMP will aggregate multiple terms containing the same variable. For example, given a constraint `2x^2 + 3x^2 <= 2`, `set_normalized_coefficient(con, [x], [x], [4])` will create the constraint `4x^2 <= 2`.

## Example

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> @constraint(model, con, 2x[1]^2 + 3 * x[1] * x[2] + x[2] <= 2)
con : 2 x[1]² + 3 x[1]*x[2] + x[2] ≤ 2

julia> set_normalized_coefficient([con, con], [x[1], x[1]], [x[1], x[2]], [4, 5])

julia> con
con : 4 x[1]² + 5 x[1]*x[2] + x[2] ≤ 2
```
