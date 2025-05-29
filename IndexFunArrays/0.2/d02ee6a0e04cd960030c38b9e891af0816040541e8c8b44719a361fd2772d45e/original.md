```
tt([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

A distance ramp along fifth (time) dimension. See `rr2` for a description of all options.

```jldoctest
julia> tt((1, 1, 1, 1, 4))
1×1×1×1×4 IndexFunArray{Float64, 5, IndexFunArrays.var"#69#72"{Float64, NTuple{5, Float64}}}:
[:, :, 1, 1, 1] =
 -2.0

[:, :, 1, 1, 2] =
 -1.0

[:, :, 1, 1, 3] =
 0.0

[:, :, 1, 1, 4] =
 1.0
```

---

```
tt(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

This is a wrapper for  `tt(eltype(arr), size(arr), scaling=scaling, offset=offset)`.
