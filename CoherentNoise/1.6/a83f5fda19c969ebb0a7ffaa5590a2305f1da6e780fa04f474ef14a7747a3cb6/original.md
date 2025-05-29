```
terrace(x::AbstractSampler, points::Vector{Pair{Float64,Float64}}; invert=false)
```

Construct a modifier sampler that outputs the result of sampling from `x` after remapping its output to a terrace-forming curve.

The curve is defined by a `Vector` of `Float64`s given by `points`. Each point represents an input and output number.

When sampling from sampler `x`, the output is evaluated using the curve data, and maps it to a new output value.

# Arguments

  * `invert`: Specify whether the curve is inverted between control points.
