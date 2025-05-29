```
xf = id_to_xf(voxel_id, n_pts)
```

与えられた `voxel_id` に対して、`Grid` 内のこのボクセルに対応する分数座標を返します。

# 引数

  * `n_pts::Tuple{Int, Int, Int}`: `Grid` の各軸に沿ったボクセルの数
  * `voxel_id::Array{Int, 1}`: `grid.data` 内のボクセル座標

# 戻り値

  * `xf::Array{Float64, 1}`: グリッドボクセルに対応する分数座標
