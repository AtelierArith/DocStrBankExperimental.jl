```
PartitionForestIterator(t::AbstractRootedTree, edge_set)
```

根付き木 `t` の [`partition_forest`](@ref) の遅延イテレータ表現。[`RootedTreeIterator`](@ref) と同様に、イテレート中にそれらを保存または変更したい場合は、内部キャッシュへのビューである可能性があるため、イテレートを `copy` する必要があります。

他に [`partition_forest`](@ref)、[`partition_skeleton`](@ref)、および [`PartitionIterator`](@ref) も参照してください。

# 参考文献

以下の第2.3節

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
