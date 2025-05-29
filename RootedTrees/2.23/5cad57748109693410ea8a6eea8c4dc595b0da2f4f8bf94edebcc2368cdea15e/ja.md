```
rootedtree!(level_sequence)
```

`level_sequence` から標準の [`RootedTree`](@ref) オブジェクトを構築します。このプロセスで `level_sequence` が変更される可能性があります。詳細は [`rootedtree`](@ref) を参照してください。

!!! warning
    これにより `level_sequence` が変更され、`level_sequence` のさらなる変更がこの関数によって返される根付き木を無効にする可能性があります。代わりに [`rootedtree`](@ref) を呼び出すことを検討してください。


# 参考文献

  * Terry Beyer and Sandra Mitchell Hedetniemi. "Constant time generation of rooted trees". SIAM Journal on Computing 9.4 (1980): 706-712. [DOI: 10.1137/0209055](https://doi.org/10.1137/0209055)
