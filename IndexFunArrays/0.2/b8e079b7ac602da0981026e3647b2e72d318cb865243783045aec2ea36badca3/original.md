```
box([::Type{T}], size::NTuple, boxsize=size./2; offset=CtrFT, scale=ScaFTEdge, dims=ntuple(+, N))
```

A multidimensional box, being one inside and zero outside. `boxsize` defines the outer dimensions of the box. To obtain box sizes for integer pixels that correspond to the Fourier-space centers both for the array and the box, an additional offset of 0.25 pixels is automatically applied and box pixels are one if less or equal to half the boxsize along this dimension.

```julia
julia> box((10,10),(3,6))
10×10 IndexFunArray{Float64, 2, IndexFunArrays.var"#g#182"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}, Int64}}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0

 julia> box((7,8))
 7×8 IndexFunArray{Float64, 2, IndexFunArrays.var"#g#182"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}, Int64}}:
  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
  0.0  0.0  1.0  1.0  1.0  1.0  0.0  0.0
  0.0  0.0  1.0  1.0  1.0  1.0  0.0  0.0
  0.0  0.0  1.0  1.0  1.0  1.0  0.0  0.0
  0.0  0.0  1.0  1.0  1.0  1.0  0.0  0.0
  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
```

---

box(arr::AbstractArray, boxsize; offset=CtrFT, scale=ScaUnit, dims=ntuple(+, N))  

This is a wrapper for  `box(eltype(arr), size(arr), boxsize; scaling=scaling, offset=offset)`.
