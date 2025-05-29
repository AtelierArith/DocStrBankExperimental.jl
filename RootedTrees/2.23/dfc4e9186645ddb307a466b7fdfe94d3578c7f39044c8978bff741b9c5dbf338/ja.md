```
SplittingIterator(t::RootedTree)
```

根付き木 `t` のすべての分割森林と部分木を反復するイテレータです。これは基本的に [`all_splittings`](@ref) のイテレータ版です。

他に [`partition_forest`](@ref) と [`partition_skeleton`](@ref) も参照してください。

# 参考文献

以下の文献のセクション 2.2

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
