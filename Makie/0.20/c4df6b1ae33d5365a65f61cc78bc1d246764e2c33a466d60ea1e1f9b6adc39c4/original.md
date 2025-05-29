```
Linestyle(value::Vector{<:Real})
```

A type that can be used as value for the `linestyle` keyword argument of plotting functions to arbitrarily customize the linestyle.

The `value` is a vector of positions where the line flips from being drawn or not and vice versa. The values of `value` are in units of linewidth.

For example, with `value = [0.0, 4.0, 6.0, 9.5]` you start drawing at 0, stop at 4 linewidths, start again at 6, stop at 9.5, then repeat with 0 and 9.5 being treated as the same position.
