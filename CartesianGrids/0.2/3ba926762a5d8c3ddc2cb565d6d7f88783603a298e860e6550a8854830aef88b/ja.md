```
product!(out::PointData,p::PointData,q::PointData)
```

点データ `p` と `q` のアダマール（すなわち、要素ごとの）積を計算し、結果を `out` に返します。`p` と `q` は、スカラーのいずれかが含まれている限り、混合型（スカラー、ベクトル、テンソル）であることができます。また、`out` は `p` と `q` の昇格された型と一致する要素型を持たなければなりません。

# 例

```jldoctest
julia> fcs = ScalarData(5,dtype=ComplexF64);

julia> fill!(fcs,2im)
5点のスカラー値を持つ Complex{Float64} データ
5-element Array{Complex{Float64},1}:
 0.0 + 2.0im
 0.0 + 2.0im
 0.0 + 2.0im
 0.0 + 2.0im
 0.0 + 2.0im

julia> frt = TensorData(fcs,dtype=Float64);

julia> fill!(frt,1.0)
5点のテンソル値を持つ Float64 データ dudx, dudy, dvdx, dvdy
5×4 Array{Float64,2}:
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0

julia> out = similar(frt,element_type=ComplexF64);

julia> product!(out,frt,fcs)
5点のテンソル値を持つ Complex{Float64} データ dudx, dudy, dvdx, dvdy
5×4 Array{Complex{Float64},2}:
 0.0+2.0im  0.0+2.0im  0.0+2.0im  0.0+2.0im
 0.0+2.0im  0.0+2.0im  0.0+2.0im  0.0+2.0im
 0.0+2.0im  0.0+2.0im  0.0+2.0im  0.0+2.0im
 0.0+2.0im  0.0+2.0im  0.0+2.0im  0.0+2.0im
 0.0+2.0im  0.0+2.0im  0.0+2.0im  0.0+2.0im
```
