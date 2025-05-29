```
set_normalized_coefficient(
    constraint::ConstraintRef,
    variable::GenericVariableRef,
    value::Number,
)
```

Set the coefficient of `variable` in the constraint `constraint` to `value`.

Note that prior to this step, JuMP will aggregate multiple terms containing the same variable. For example, given a constraint `2x + 3x <= 2`, `set_normalized_coefficient(con, x, 4)` will create the constraint `4x <= 2`.

## Example

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, con, 2x + 3x <= 2)
con : 5 x ≤ 2

julia> set_normalized_coefficient(con, x, 4)

julia> con
con : 4 x ≤ 2
```
