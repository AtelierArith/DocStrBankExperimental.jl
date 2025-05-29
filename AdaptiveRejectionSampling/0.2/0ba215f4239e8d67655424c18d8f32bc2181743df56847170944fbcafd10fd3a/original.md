```
Envelop(lines::Vector{Line}, support::Tuple{Float64, Float64})
```

A piecewise linear function with k segments defined by the lines `L_1, ..., L_k` and cutpoints `c_1, ..., c_k+1` with `c1 = support[1]` and `c2 = support[2]`. A line L*k is active in the segment [c*k, c*k+1], and it's assigned a weight w*k based on [exp_integral](@exp_integral). The weighted integral over c*1 to c*k+1 is one, so that the envelop is interpreted as a density.
