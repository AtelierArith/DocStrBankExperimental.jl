```
setsym_oop(indp, sym)
```

Return a function which takes a value provider `valp` and a value `val`, and returns `state_values(valp), parameter_values(valp)` with the states/parameters in `sym` set to the corresponding values in `val`. This allows changing the types of values stored, and leverages [`remake_buffer`](@ref). Note that `sym` can be an index, a symbolic variable, or an array/tuple of the aforementioned. All entries `s` in `sym` must satisfy `is_variable(indp, s)` or `is_parameter(indp, s)`.

Requires that the value provider implement `state_values`, `parameter_values` and `remake_buffer`.
