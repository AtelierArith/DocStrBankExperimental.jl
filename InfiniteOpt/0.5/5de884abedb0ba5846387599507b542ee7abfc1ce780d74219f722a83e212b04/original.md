```
JuMP.set_normalized_coefficient(cref::InfOptConstraintRef,
                                variable::GeneralVariableRef,
                                value::Real)::Nothing
```

Set the coefficient of `variable` in the constraint `constraint` to `value`. Note that prior to this step, JuMP will aggregate multiple terms containing the same variable. For example, given a constraint `2x + 3x <= 2`, `set_normalized_coefficient(con, x, 4)` will create the constraint `4x <= 2`.

```julia-repl
julia> con
con : 5 x ≤ 2.0

julia> set_normalized_coefficient(con, x, 4)

julia> con
con : 4 x ≤ 2.0
```
