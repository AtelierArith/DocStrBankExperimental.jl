```
delta([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

A `delta` peak positioned at offset. See `rr2()` for a description of all options.  Note that `scale` does not influence the result. Also note that this function operates on a comparison for equality, which means a sub-pixel offset of the delta results into zero.

```jldoctest
julia> delta((5,5))
5×5 IndexFunArray{Float64, 2, IndexFunArrays.var"#79#81"{Float64, Tuple{Float64, Float64}}}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> delta((6,6))
6×6 IndexFunArray{Float64, 2, IndexFunArrays.var"#79#81"{Float64, Tuple{Float64, Float64}}}:
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0

 julia> delta((5,5),offset=CtrCorner)
 5×5 IndexFunArray{Float64, 2, IndexFunArrays.var"#79#81"{Float64, Tuple{Float64, Float64}}}:
  1.0  0.0  0.0  0.0  0.0
  0.0  0.0  0.0  0.0  0.0
  0.0  0.0  0.0  0.0  0.0
  0.0  0.0  0.0  0.0  0.0
  0.0  0.0  0.0  0.0  0.0
  
```

---

```
delta(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

This is a wrapper for  `delta(eltype(arr), size(arr), scaling=scaling, offset=offset)`.
