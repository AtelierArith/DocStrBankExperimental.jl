```julia
linterp1!(yq::StridedArray, x::AbstractArray, y::AbstractArray, xq; extrapolate=:Linear, knot_index=ones(Int, length(xq)))
```

`linterp1`のインプレースバリアント。
