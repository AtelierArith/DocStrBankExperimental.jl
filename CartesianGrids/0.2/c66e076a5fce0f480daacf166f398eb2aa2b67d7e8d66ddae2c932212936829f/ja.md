```
VectorData <: PointData
```

二成分ベクトル値データの一次元配列のラッパーです。結果として得られるラッパーは、最初の成分と第二の成分が重ねられているかのようにインデックス指定できます。

# コンストラクタ

  * `VectorData(d::AbstractVector[,dtype=Float64])` は、データ `d` の一次元配列のラッパーを構築し、`d` を `u` と `v` の成分に均等に分割します。
  * `VectorData(u::AbstractVector,v::AbstractVector)` は、ベクトル成分データ `u` と `v` のラッパーを構築します。
  * `VectorData(n::Int)` は、両方の成分の長さ `n` のゼロで構成されたラッパーを構築します。
  * `VectorData(x::PointData)` は、`x` にラップされたのと同じ長さのゼロ成分のラッパーを構築します。
  * `VectorData(n::Int,dtype=ComplexF64)` は、両方の成分の長さ `n` の複素値ゼロで構成されたラッパーを構築します。

# 例

```jldoctest
julia> f = VectorData(10,dtype=ComplexF64);

julia> f.v[1:5] = 1:5;

julia> f
10 points of vector-valued Complex{Float64} data
10×2 Array{Complex{Float64},2}:
 0.0+0.0im  1.0+0.0im
 0.0+0.0im  2.0+0.0im
 0.0+0.0im  3.0+0.0im
 0.0+0.0im  4.0+0.0im
 0.0+0.0im  5.0+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im

julia> f[7] = 1im; f[18] = 0.2;

julia> f
10 points of vector-valued Complex{Float64} data
10×2 Array{Complex{Float64},2}:
 0.0+0.0im  1.0+0.0im
 0.0+0.0im  2.0+0.0im
 0.0+0.0im  3.0+0.0im
 0.0+0.0im  4.0+0.0im
 0.0+0.0im  5.0+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+1.0im  0.0+0.0im
 0.0+0.0im  0.2+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im
```
