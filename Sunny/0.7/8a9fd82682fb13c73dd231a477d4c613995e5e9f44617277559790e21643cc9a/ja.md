```
print_irreducible_bz_paths(cryst::Crystal)
```

特定の高対称点とそれらの間の推奨経路を印刷します。これらの点は、結晶の点群対称性によって第1ブリルアンゾーンから縮小された不可約ブリルアンゾーンにあります。座標は逆格子単位（RLU）で印刷され、すなわち`cryst`の従来の格子ベクトルの倍数として表されます。これらの高対称経路は、元々文献[1]で定式化され、[SeeK-path](https://github.com/giovannipizzi/seekpath)に実装されました。Sunnyはこの機能を[Brillouin.jl](https://github.com/thchr/Brillouin.jl)パッケージから取得します。

これらの高対称経路のインタラクティブな視覚化については、[`view_bz`](@ref)も参照してください。

## 参考文献

1. [Y. Hinuma, G. Pizzi, Y. Kumagai, F. Oba, I. Tanaka, *結晶学に基づくバンド構造図経路*, Comp. Mat. Sci. **128**, 140 (2017)](https://doi.org/10.1016/j.commatsci.2016.10.015).
