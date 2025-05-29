```
ScalarData <: PointData
```

スカラー値データの一次元配列のラッパーです。結果として得られるラッパーは、配列自体と同じ方法でインデックス指定できます。

# コンストラクタ

  * `ScalarData(d::AbstractVector[,dtype=Float64])` は、データ `d` の一次元配列のラッパーを構築します。
  * `ScalarData(n::Int)` は、長さ `n` のゼロの配列のラッパーを構築します。
  * `ScalarData(x::PointData)` は、`x` にラップされたものと同じ長さのゼロの配列のラッパーを構築します。
  * `ScalarData(n::Int,dtype=ComplexF64)` は、複素値データのラッパーを構築します。
  * `ScalarData(x::PointData,dtype=ComplexF64)` は、`x` にラップされたものと同じ長さの複素ゼロの配列のラッパーを構築します。

# 例

```jldoctest
julia> f = ScalarData(10);

julia> f[5] = 1.0;

julia> f
10 points of scalar-valued Float64 data
10-element Array{Float64,1}:
 0.0
 0.0
 0.0
 0.0
 1.0
 0.0
 0.0
 0.0
 0.0
 0.0
```
