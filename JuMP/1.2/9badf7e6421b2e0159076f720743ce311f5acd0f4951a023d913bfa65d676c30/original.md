```
set_normalized_rhs(con_ref::ConstraintRef, value)
```

Set the right-hand side term of `constraint` to `value`.

Note that prior to this step, JuMP will aggregate all constant terms onto the right-hand side of the constraint. For example, given a constraint `2x + 1 <= 2`, `set_normalized_rhs(con, 4)` will create the constraint `2x <= 4`, not `2x + 1 <= 4`.

```jldoctest; setup = :(using JuMP; model = Model(); @variable(model, x)), filter=r"≤|<="
julia> @constraint(model, con, 2x + 1 <= 2)
con : 2 x <= 1.0

julia> set_normalized_rhs(con, 4)

julia> con
con : 2 x <= 4.0
```
