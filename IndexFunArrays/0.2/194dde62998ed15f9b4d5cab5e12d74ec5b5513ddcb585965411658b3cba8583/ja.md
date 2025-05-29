```
ramp(::Type{T}, dim::Int, dim_size::Int;
    offset=CtrFT, scale=ScaUnit,
    weight=1,
    accumulator=sum) where {T}
```

`dim_size`のサイズを持つ`dim`次元のランプを生成し、多次元式を通じてブロードキャストに使用されます。`dim`は生成される向きの配列の最も高い次元です。これがランプの方向でもあります。`dim_size`はこの次元に沿ったサイズです。

オフセットとスケールおよび次元の詳細についてはrr2を参照してください。

```jldoctest
julia> ramp(Float32, 1, 7; offset=(2,))
7-element IndexFunArray{Float32, 1, IndexFunArrays.var"#434#435"{Tuple{Int64}, Tuple{Int64}, Int64}}:
 -1
  0
  1
  2
  3
  4
  5
```

ramp(dim::Int, dim_size::Int; offset=CtrFt, scaling=ScaUnit)

これは`ramp(Float64, dim::Int, dim_size::Int; offset=CtrFt, scaling=ScaUnit)`のラッパーです。
