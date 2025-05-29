```
ee([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

A distance ramp along forth (element) dimension. This dimension is often used as a color or wavelength channel. See `rr2` for a description of all options.

```jldoctest
julia> ee((1, 1, 1, 4))
1×1×1×4 IndexFunArray{Float64, 4, IndexFunArrays.var"#60#63"{Float64, NTuple{4, Float64}}}:
[:, :, 1, 1] =
 -2.0

[:, :, 1, 2] =
 -1.0

[:, :, 1, 3] =
 0.0

[:, :, 1, 4] =
 1.0
```

---

```
ee(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

This is a wrapper for  `ee(eltype(arr), size(arr), scaling=scaling, offset=offset)`.
