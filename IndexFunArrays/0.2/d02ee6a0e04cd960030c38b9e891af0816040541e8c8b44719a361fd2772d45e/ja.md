```
tt([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

時間次元の5番目に沿った距離ランプ。すべてのオプションの説明については `rr2` を参照してください。

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

これは `tt(eltype(arr), size(arr), scaling=scaling, offset=offset)` のラッパーです。
