```
zz([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

A distance ramp along third dimension. See `rr2` for a description of all options.

```jldoctest
julia> zz((1, 1, 4))
1×1×4 IndexFunArray{Float64, 3, IndexFunArrays.var"#24#25"{Float64, Tuple{Float64, Float64, Float64}, Tuple{Int64, Int64, Int64}}}:
[:, :, 1] =
 -2.0

[:, :, 2] =
 -1.0

[:, :, 3] =
 0.0

[:, :, 4] =
 1.0
```

---

```
zz(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

This is a wrapper for  `zz(eltype(arr), size(arr), scaling=scaling, offset=offset)`.
