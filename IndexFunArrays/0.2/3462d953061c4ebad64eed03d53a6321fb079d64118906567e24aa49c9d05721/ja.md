```
delta([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

オフセットに位置する `delta` ピーク。すべてのオプションの説明については `rr2()` を参照してください。 `scale` は結果に影響を与えないことに注意してください。また、この関数は等価性の比較に基づいて動作するため、デルタのサブピクセルオフセットはゼロになります。

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

これは `delta(eltype(arr), size(arr), scaling=scaling, offset=offset)` のラッパーです。
