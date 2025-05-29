```
reverse_dim!(var::OutputVar, dim_name)
```

Like [`reverse_dim`](@ref), but operates in-place in `var`.

This function is helpful if the order of a dimension need to be reversed, so that an interpolant can be made.
