```
JuMP.add_to_function_constant(cref::InfOptConstraintRef, value::Real)::Nothing
```

Add `value` to the function constant term. Note that for scalar constraints, JuMP will aggregate all constant terms onto the right-hand side of the constraint so instead of modifying the function, the set will be translated by `-value`. For example, given a constraint `2x <= 3`, `add_to_function_constant(c, 4)` will modify it to `2x <= -1`. ```
