```
get_dof_map(space::FESpace) -> VectorDofMap
```

座標順にソートされたアクティブな自由度（dof）を、すべての次元について返します。`space` が D 次元のスカラー `FESpace` の場合、出力インデックスマップは `AbstractDofMap{<:Integer,D}` のサブタイプになります。`space` が D 次元のベクトル値 `FESpace` の場合、出力インデックスマップは `AbstractDofMap{D+1}` のサブタイプになります。
