```
partition_forest(t::RootedTree, edge_set)
```

根付き木 `t` の分割フォレストを形成します。`edge_set` で `false` とマークされたエッジが削除されます。ブールイテラブル `edge_set` の i 番目の値は、レベルシーケンスのノード `i+1` をその親に接続するエッジに対応します。

[`partition_skeleton`](@ref)、[`PartitionIterator`](@ref)、および [`PartitionForestIterator`](@ref) も参照してください。

# 参考文献

以下の第2.3節

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
