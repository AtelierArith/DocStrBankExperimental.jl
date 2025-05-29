```
nm_measurement(probability, vertexset)
```

`vertexset` に従った実数値の確率ベクトル `probability` の結合確率を返します。

*注:* 適切な確率ベクトルを提供するのはユーザーの責任です。

# 例

```jldoctest; setup = :(using QSWalk)
julia> probability = [0.05, 0.1, 0.25, 0.3, 0.01, 0.20, 0.04, 0.05]
8-element Array{Float64,1}:
 0.05
 0.1
 0.25
 0.3
 0.01
 0.2
 0.04
 0.05

julia> nm_measurement(probability, VertexSet([[1, 4], [2, 3, 5], [6], [7, 8]]))
4-element Array{Float64,1}:
 0.35
 0.36
 0.2
 0.09
```
