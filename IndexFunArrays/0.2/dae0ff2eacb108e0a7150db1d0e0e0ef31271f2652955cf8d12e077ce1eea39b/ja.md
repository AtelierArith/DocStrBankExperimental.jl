```
yy([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

第二次元に沿った距離ランプ。すべてのオプションの説明については `rr2` を参照してください。

```jldoctest
julia> yy((4,4))
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#19#20"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 -2.0  -1.0  0.0  1.0
 -2.0  -1.0  0.0  1.0
 -2.0  -1.0  0.0  1.0
 -2.0  -1.0  0.0  1.0
```

---

```
yy(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

これは `yy(eltype(arr), size(arr), scaling=scaling, offset=offset)` のラッパーです。
