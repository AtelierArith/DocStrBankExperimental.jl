```
null1(N::BinaryNetwork)
```

ネットワーク `N` が与えられた場合、`null1(N)` は同じ次元のネットワークを返し、すべての相互作用は `N` の接続性に等しい確率で発生します。

これはネットワークが退化していないことを保証するものではないため、この分析の出力は `is_degenerate` を使用してフィルタリングするか、`simplify` に渡すべきです。このアプローチの出力は、常に元のネットワークと同じ部分性を持つ確率的ネットワークです。

#### 参考文献

Fortuna, M.A., Bascompte, J., 2006. Habitat loss and the structure of plantanimal mutualistic networks. Ecol. Lett. 9, 281–286. https://doi.org/10.1111/j.1461-0248.2005.00868.x
