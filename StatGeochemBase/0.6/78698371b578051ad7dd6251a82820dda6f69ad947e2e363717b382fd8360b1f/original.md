```julia
linterp1s!(yq::StridedArray, x::StridedArray, y::StridedArray, xq; extrapolate=:Linear)
linterp1s!(yq::StridedArray, knot_index::StridedArray{Int}, x::StridedArray, y::StridedArray, xq::AbstractArray; extrapolate=:Linear)
```

In-place variant of `linterp1s`. Will sort `x` and permute `y` to match, before interpolating at `xq` and storing the result in `yq`.

An optional temporary working array `knot_index = similar(xq, Int)` may be provided to fully eliminate allocations.
