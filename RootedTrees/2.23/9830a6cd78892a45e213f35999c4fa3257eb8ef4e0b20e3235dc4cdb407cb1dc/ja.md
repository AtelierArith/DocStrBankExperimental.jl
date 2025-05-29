```
RootedTree(level_sequence, is_canonical::Bool=false)
```

レベルシーケンスを使用して根付き木を表します。

!!! warning
    これは低オーバーヘッドで安全でないコンストラクタです。代わりに[`rootedtree`](@ref)を呼び出すことを検討してください。


# 参考文献

  * Terry Beyer and Sandra Mitchell Hedetniemi. "Constant time generation of rooted trees". SIAM Journal on Computing 9.4 (1980): 706-712. [DOI: 10.1137/0209055](https://doi.org/10.1137/0209055)
