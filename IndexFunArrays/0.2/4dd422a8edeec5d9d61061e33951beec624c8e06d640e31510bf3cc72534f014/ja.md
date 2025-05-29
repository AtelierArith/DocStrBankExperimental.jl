```
idx([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit)
```

すべてのオプションの説明については `rr2` を参照してください。

基本的には `CartesianIndices` をタプルとして返しますが、オプションの `scale`、`offset`、およびデータ型を考慮しています。返されるタプルの要素に対して `T` が要素ごとに強制されることに注意してください。

```jldoctest
julia> idx(Int, (3,3), offset=CtrCorner)
3×3 IndexFunArray{Tuple{Int64, Int64}, 2, IndexFunArrays.var"#39#40"{Int64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 (0, 0)  (0, 1)  (0, 2)
 (1, 0)  (1, 1)  (1, 2)
 (2, 0)  (2, 1)  (2, 2)

julia> idx(Int, (3,3), offset=(0,0))
3×3 IndexFunArray{Tuple{Int64, Int64}, 2, IndexFunArrays.var"#39#40"{Int64, Tuple{Int64, Int64}, Tuple{Int64, Int64}}}:
 (1, 1)  (1, 2)  (1, 3)
 (2, 1)  (2, 2)  (2, 3)
 (3, 1)  (3, 2)  (3, 3)

julia> idx(Float32, (3,3), offset=(0,0))
3×3 IndexFunArray{Tuple{Float32, Float32}, 2, IndexFunArrays.var"#39#40"{Float32, Tuple{Int64, Int64}, Tuple{Int64, Int64}}}:
 (1.0, 1.0)  (1.0, 2.0)  (1.0, 3.0)
 (2.0, 1.0)  (2.0, 2.0)  (2.0, 3.0)
 (3.0, 1.0)  (3.0, 2.0)  (3.0, 3.0)
```
