```
all_partitions(t::RootedTree)
```

根付き木 `t` のすべての分割森林とスケルトンを作成します。これは、すべての可能な辺の集合をループする際に [`partition_forest`](@ref) と [`partition_skeleton`](@ref) の戻り値のベクトルを返します。

また、[`PartitionIterator`](@ref) も参照してください。

# 参考文献

以下の文献のセクション 2.3

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)

```
