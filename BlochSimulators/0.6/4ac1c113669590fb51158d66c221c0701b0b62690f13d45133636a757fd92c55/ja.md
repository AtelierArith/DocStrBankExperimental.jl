```
make_coordinates(x::T, y::T, z::T) where {T<:AbstractArray{<:Real}}
```

配列 `x`、`y`、および `z` から座標の3Dメッシュグリッドを作成し、それをStructArrayとして返します。

# 引数

  * `x::T`: ボクセルごとのx座標の配列。
  * `y::T`: ボクセルごとのy座標の配列。
  * `z::T`: ボクセルごとのz座標の配列。
