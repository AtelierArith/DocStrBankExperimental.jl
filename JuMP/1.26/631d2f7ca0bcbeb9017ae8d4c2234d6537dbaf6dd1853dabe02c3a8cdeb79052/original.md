```
set_normalized_coefficient(
    con_ref::ConstraintRef,
    variable::AbstractVariableRef,
    new_coefficients::Vector{Tuple{Int64,T}},
)
```

Set the coefficients of `variable` in the constraint `con_ref` to `new_coefficients`, where each element in `new_coefficients` is a tuple which maps the row to a new coefficient.

Note that prior to this step, during constraint creation, JuMP will aggregate multiple terms containing the same variable.

## Example

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, con, [2x + 3x, 4x] in MOI.Nonnegatives(2))
con : [5 x, 4 x] ∈ MathOptInterface.Nonnegatives(2)

julia> set_normalized_coefficient(con, x, [(1, 2.0), (2, 5.0)])

julia> con
con : [2 x, 5 x] ∈ MathOptInterface.Nonnegatives(2)
```
