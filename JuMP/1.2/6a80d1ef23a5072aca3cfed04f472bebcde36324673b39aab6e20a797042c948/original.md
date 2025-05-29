```
set_normalized_coefficients(
    con_ref::ConstraintRef,
    variable,
    new_coefficients::Vector{Tuple{Int64,T}},
)
```

Set the coefficients of `variable` in the constraint `con_ref` to `new_coefficients`, where each element in `new_coefficients` is a tuple which maps the row to a new coefficient.

Note that prior to this step, during constraint creation, JuMP will aggregate multiple terms containing the same variable.

```jldoctest; setup = :(using JuMP), filter=r"≤|<="
model = Model()
@variable(model, x)
@constraint(model, con, [2x + 3x, 4x] in MOI.Nonnegatives(2))
set_normalized_coefficients(con, x, [(1, 2.0), (2, 5.0)])
con

# output

con : [2 x, 5 x] ∈ MathOptInterface.Nonnegatives(2)
```
