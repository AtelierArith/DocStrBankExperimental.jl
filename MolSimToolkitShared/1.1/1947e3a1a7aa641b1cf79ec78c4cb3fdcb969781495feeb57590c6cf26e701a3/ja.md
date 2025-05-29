```
rmsd(x::AbstractVector,y::AbstractVector)
```

2つの座標ベクトル間の二乗平均平方根偏差を計算します。

# 引数

  * `x::AbstractVector`: 座標のベクトル。
  * `y::AbstractVector`: 座標のベクトル。

# 戻り値

  * `rmsd::Real`: 2つのベクトル間の二乗平均平方根偏差。

```jldoctest
julia> import MolSimToolkitShared: rmsd

julia> x = [ [1.0, 2.0, 3.0], [4.0, 5.0, 6.0], [7.0, 8.0, 9.0] ];

julia> y = [ [2.0, 3.0, 4.0], [4.0, 5.0, 6.0], [7.0, 8.0, 9.0] ];

julia> rmsd(x, y)
1.0
```
