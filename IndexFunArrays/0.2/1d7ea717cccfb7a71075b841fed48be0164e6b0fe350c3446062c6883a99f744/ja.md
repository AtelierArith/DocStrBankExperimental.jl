```
zz([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

第三次元に沿った距離ランプ。すべてのオプションの説明については `rr2` を参照してください。

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

これは `zz(eltype(arr), size(arr), scaling=scaling, offset=offset)` のラッパーです。
