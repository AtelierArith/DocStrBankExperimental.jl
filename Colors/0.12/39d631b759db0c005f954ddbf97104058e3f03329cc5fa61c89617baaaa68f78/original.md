```
colordiff(a, b; metric=DE_2000())
```

Compute an approximate measure of the perceptual difference between colors `a` and `b`. Optionally, a `metric` may be supplied, chosen among [`DE_2000`](@ref) (the default), [`DE_94`](@ref), [`DE_JPC79`](@ref), [`DE_CMC`](@ref), [`DE_BFD`](@ref), [`DE_AB`](@ref), [`DE_DIN99`](@ref), [`DE_DIN99d`](@ref) and [`DE_DIN99o`](@ref).

The return value is a non-negative number in a type depending on the colors and metric.

!!! note
    The supported metrics measure the difference within `Lab` or its variant colorspaces. When the input colors are not in the colorspace internally used by the metric, the colors (e.g. in `RGB`) are converted with the default whitepoint CIE D65 (`Colors.WP_D65`). If you want to use another whitepoint, convert the colors into the colorspace used by metric (e.g. `Lab` for [`DE_2000`](@ref)) in advance.

