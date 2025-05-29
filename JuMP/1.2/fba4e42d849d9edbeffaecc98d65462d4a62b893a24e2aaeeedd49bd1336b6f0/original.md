```
set_normalized_coefficient(con_ref::ConstraintRef, variable::VariableRef, value)
```

Set the coefficient of `variable` in the constraint `constraint` to `value`.

Note that prior to this step, JuMP will aggregate multiple terms containing the same variable. For example, given a constraint `2x + 3x <= 2`, `set_normalized_coefficient(con, x, 4)` will create the constraint `4x <= 2`.

```jldoctest; setup = :(using JuMP), filter=r"≤|<="
model = Model()
@variable(model, x)
@constraint(model, con, 2x + 3x <= 2)
set_normalized_coefficient(con, x, 4)
con

# output

con : 4 x <= 2.0
```
