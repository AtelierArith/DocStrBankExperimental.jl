```
weighted_color_mean(weights, colors)
```

Returns the weighted mean of the given collection `colors` with `weights`. This is semantically equivalent to the calculation of `sum(weights .* colors)`.

# Examples

```jldoctest; setup = :(using Colors, FixedPointNumbers)
julia> rgbs = (RGB(1, 0, 0), RGB(0, 1, 0), RGB(0, 0, 1));

julia> weighted_color_mean([0.2, 0.2, 0.6], rgbs)
RGB{N0f8}(0.2, 0.2, 0.6)

julia> weighted_color_mean(0.5:-0.25:0.0, RGB{Float64}.(rgbs))
RGB{Float64}(0.5, 0.25, 0.0)
```

!!! compat "Colors v0.13"
    `wighted_color_mean` with collection or iterator inputs requires Colors v0.13 or later.


!!! note
    In a cylindrical color space such as HSV, a weighted mean of more than three colors is generally not meaningful.

