```
curve(x::AbstractSampler, points::Vector{Pair{Float64,Float64}})
```

Construct a modifier sampler that outputs the result of sampling from `x` after remapping its output to an arbitrary curve.

The curve is defined by a `Vector` of `Pair`s given by `points`. Each pair of points represents an input and output number. The curve is a cubic spline, and so `points` must contain a list of four point pairs at a minimum. Additionally, no two point pairs can contain the same input point value.

When sampling from sampler `x`, the output is evaluated using the curve data, and maps it to a new output value.
