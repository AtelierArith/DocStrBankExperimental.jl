```
partition_skeleton(t::AbstractRootedTree, edge_set)
```

根付き木 `t` のパーティションスケルトンを形成します。つまり、パーティションフォレストの各木を単一の頂点に収縮し、パーティションフォレストを得るために削除されたエッジを再確立した根付き木を得ます。

[`partition_forest`](@ref) および [`PartitionIterator`](@ref) も参照してください。

# 参考文献

以下の文献のセクション 2.3（および色付き木についてはセクション 6.1）：

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
