```
update_density!(grid, molecule, species)
```

は、分子の配列に基づいて密度グリッドを更新します。分子が指定された種と一致しない場合、それは密度グリッドに追加されません。この関数は実際の密度を計算するものではなく、GCMCシミュレーションの最後に `./ = num_snapshots` が必要です。

# 引数

  * `grid::Grid`: 更新されるグリッド
  * `molecules::Array{Molecule, 1}`: グリッドに追加される分子の位置を持つ配列
  * `species::Symbol`: この密度グリッドに追加できる原子の種
