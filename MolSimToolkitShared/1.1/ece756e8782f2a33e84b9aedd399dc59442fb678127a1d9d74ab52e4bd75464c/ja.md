```
center_of_mass(x::AbstractVector{<:AbstractVector}[, mass::AbstractVector=nothing])
```

点の集合の重心を計算します。

# 引数

  * `x::AbstractVector{<:AbstractVector}`: 座標のベクトル。
  * `mass::AbstractVector`: 質量のベクトル。提供されない場合、すべての質量は等しいと見なされます。

# 例

```jldoctest
julia> import MolSimToolkitShared: center_of_mass

julia> x = [ [1.0, 2.0, 3.0], [4.0, 5.0, 6.0], [7.0, 8.0, 9.0] ];

julia> center_of_mass(x)
3-element Vector{Float64}:
 4.0
 5.0
 6.0

julia> center_of_mass(x, [1.0, 2.0, 3.0]) # 質量を提供する
3-element Vector{Float64}:
 5.0
 6.0
 7.0

```
