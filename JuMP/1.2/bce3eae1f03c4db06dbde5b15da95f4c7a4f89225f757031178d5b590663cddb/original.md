```
set_string_names_on_creation(model::Model, value::Bool)
```

Set the default argument of the `set_string_name` keyword in the [`@variable`](@ref) and [`@constraint`](@ref) macros to `value`. This is used to determine whether to assign `String` names to all variables and constraints in `model`.

By default, `value` is `true`. However, for larger models calling `set_string_names_on_creation(model, false)` can improve performance at the cost of reducing the readability of printing and solver log messages.
