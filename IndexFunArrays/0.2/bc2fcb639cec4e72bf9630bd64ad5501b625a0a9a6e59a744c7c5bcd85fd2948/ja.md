```
xx([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

最初の次元に沿った距離ランプ。すべてのオプションの説明については `rr2` を参照してください。

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

これは `xx(eltype(arr), size(arr), scaling=scaling, offset=offset)` のラッパーです。
