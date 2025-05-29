```
ee([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

距離ランプは前方（要素）次元に沿っています。この次元は、色または波長チャネルとしてよく使用されます。すべてのオプションの説明については `rr2` を参照してください。

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

これは `ee(eltype(arr), size(arr), scaling=scaling, offset=offset)` のラッパーです。
