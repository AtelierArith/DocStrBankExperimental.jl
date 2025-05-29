```
xx([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

A distance ramp along first dimension. See `rr2` for a description of all options.

```jldoctest
julia> xx((4,4))
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#14#15"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 -2.0  -2.0  -2.0  -2.0
 -1.0  -1.0  -1.0  -1.0
  0.0   0.0   0.0   0.0
  1.0   1.0   1.0   1.0
```

---

```
xx(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

This is a wrapper for  `xx(eltype(arr), size(arr), scaling=scaling, offset=offset)`.
