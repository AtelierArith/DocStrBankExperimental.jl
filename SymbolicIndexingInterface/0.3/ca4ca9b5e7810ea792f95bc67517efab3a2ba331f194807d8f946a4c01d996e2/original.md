```
setp(indp, sym)
```

Return a function that takes a value provider and a value, and sets the parameter `sym` to that value. Note that `sym` can be an index, a symbolic variable, or an array/tuple of the aforementioned.

Requires that the value provider implement [`parameter_values`](@ref) and the returned collection be a mutable reference to the parameter object. In case `parameter_values` cannot return such a mutable reference, or additional actions need to be performed when updating parameters, [`set_parameter!`](@ref) must be implemented.
