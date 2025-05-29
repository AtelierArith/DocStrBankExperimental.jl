```
rr([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

`rr2`のすべてのオプションの説明を参照してください。

# 例

```jldoctest
julia> rr((3, 3))
3×3 IndexFunArray{Float64, 2, IndexFunArrays.var"#9#10"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 1.41421  1.0  1.41421
 1.0      0.0  1.0
 1.41421  1.0  1.41421

julia> rr((3, 3), offset=CtrCorner)
3×3 IndexFunArray{Float64, 2, IndexFunArrays.var"#9#10"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 0.0  1.0      2.0
 1.0  1.41421  2.23607
 2.0  2.23607  2.82843
```

---

```
rr(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

これは `rr(eltype(arr), size(arr), scaling=scaling, offset=offset)` のラッパーです。
