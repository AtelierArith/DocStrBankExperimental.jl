```
rootedtree(level_sequence, color_sequence)
```

`level_sequence` と `color_sequence` から標準の [`ColoredRootedTree`](@ref) オブジェクトを構築します。すなわち、木の各ノードのレベルを表す整数のベクトルと、関連する色（例えば、`Bool` または `Integer`）のベクトルです。

# 参考文献

  * Terry Beyer と Sandra Mitchell Hedetniemi. "Constant time generation of rooted trees". SIAM Journal on Computing 9.4 (1980): 706-712. [DOI: 10.1137/0209055](https://doi.org/10.1137/0209055)
