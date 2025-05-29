```
PartitionIterator(t::AbstractRootedTree)
```

根付き木 `t` のすべての分割フォレストとスケルトンを反復するイテレータです。これは基本的に [`all_partitions`](@ref) の純粋なイテレータ版です。特に、分割フォレストはイテレータとしてのみ実現される場合があります。[`RootedTreeIterator`](@ref) と同様に、反復中にそれらを保存または変更したい場合は、内部キャッシュへのビューである可能性があるため、イテレートを `copy` する必要があります。

また、[`partition_forest`](@ref)、[`partition_skeleton`](@ref)、および [`PartitionForestIterator`](@ref) も参照してください。

# 参考文献

以下の文献のセクション 2.3

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
