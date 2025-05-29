```
ColoredRootedTree(level_sequence, color_sequence, is_canonical::Bool=false)
```

レベルシーケンスを使用して色付き根付き木を表します。単色バージョンは [`RootedTree`](@ref) です。

他に [`BicoloredRootedTree`](@ref)、[`rootedtree`](@ref) も参照してください。

!!! warning
    これは低オーバーヘッドで安全でないコンストラクタです。代わりに [`rootedtree`](@ref) を呼び出すことを検討してください。


# 参考文献

  * Terry Beyer と Sandra Mitchell Hedetniemi. "Constant time generation of rooted trees". SIAM Journal on Computing 9.4 (1980): 706-712. [DOI: 10.1137/0209055](https://doi.org/10.1137/0209055)
  * A. L. Araujo, A. Murua, と J. M. Sanz-Serna. "Symplectic Methods Based on Decompositions". SIAM Journal on Numerical Analysis 34.5 (1997): 1926–1947. [DOI: 10.1137/S0036142995292128](https://doi.org/10.1137/S0036142995292128)
