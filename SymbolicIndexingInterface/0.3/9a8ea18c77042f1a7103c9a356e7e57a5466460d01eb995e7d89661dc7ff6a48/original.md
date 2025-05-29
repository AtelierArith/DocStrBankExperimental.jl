```
setp_oop(indp, sym)
```

Return a function which takes a value provider `valp` and a value `val`, and returns `parameter_values(valp)` with the parameters at `sym` set to `val`. This allows changing the types of values stored, and leverages [`remake_buffer`](@ref). Note that `sym` can be an index, a symbolic variable, or an array/tuple of the aforementioned.

Requires that the value provider implement `parameter_values` and `remake_buffer`.
