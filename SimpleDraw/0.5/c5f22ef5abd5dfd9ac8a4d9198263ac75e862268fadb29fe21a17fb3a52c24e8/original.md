```
get_i_max(image::AbstractMatrix)
```

Return the last index of `image` along the i-axis (vertical-axis, 1st-axis).

# Examples

```julia-repl
julia> get_i_max(falses(32, 64))
32
```
