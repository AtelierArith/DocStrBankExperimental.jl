```julia
linterp1!(yq::StridedArray, x::AbstractArray, y::AbstractArray, xq; extrapolate=:Linear, knot_index=ones(Int, length(xq)))
```

In-place variant of `linterp1`.
