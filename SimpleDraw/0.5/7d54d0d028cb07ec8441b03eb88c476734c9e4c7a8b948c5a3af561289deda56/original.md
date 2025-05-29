```
get_j_max(image::AbstractMatrix)
```

Return the last index of `image` along the j-axis (horizontal-axis, 2nd-axis).

# Examples

```julia-repl
julia> get_j_max(falses(32, 64))
64
```
