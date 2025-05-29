```
disc([::Type{T}], size::NTuple, disc_radius; offset=CtrFT, scale=ScaFTEdge, dims=ntuple(+, N))
```

A multidimensional disc (i.e. a disk in 2D and a filled sphere in 3D), being one inside and zero outside. `disc_radius` defines the radius of the disc.  The default result datatype is Float64. An alternative to generating a disc would be the edge-window.

```jldoctest
julia> disc((10,10),(3,5))
10×10 IndexFunArray{Float64, 2, IndexFunArrays.var"#g#194"{Float64, Tuple{Int64, Int64}, Tuple{Float64, Float64}, Int64}}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  0.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  0.0
 0.0  0.0  0.0  0.0  0.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0

 julia> disc((11,8),(0.5,0.5),scale=ScaFT)
11×8 IndexFunArray{Float64, 2, IndexFunArrays.var"#g#194"{Float64, Tuple{Int64, Int64}, Tuple{Float64, Float64}, Int64}}:
 0.0  0.0  0.0  1.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  0.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 0.0  0.0  1.0  1.0  1.0  1.0  1.0  0.0
 0.0  0.0  0.0  1.0  1.0  1.0  0.0  0.0
```

---

disc(arr::AbstractArray, disc_radius; offset=CtrFT, scale=ScaUnit, dims=ntuple(+, N))  

This is a wrapper for  `disc(eltype(arr), size(arr), disc_radius; scaling=scaling, offset=offset)`.
