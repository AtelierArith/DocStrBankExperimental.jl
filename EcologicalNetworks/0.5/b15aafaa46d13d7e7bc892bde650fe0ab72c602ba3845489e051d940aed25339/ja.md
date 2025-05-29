```
null2(N::BinaryNetwork)
```

ネットワーク `N` が与えられた場合、`null2(N)` は、各種の次数に等しい確率で相互作用が発生する同じ次元のネットワークを返します。

これはネットワークが退化していないことを保証するものではないため、この分析の出力は `is_degenerate` を使用してフィルタリングするか、`simplify` に渡すべきです。このアプローチの出力は、元のネットワークと同じ部分性を持つ確率的ネットワークであることが *常に* です。

#### 参考文献

Bascompte, J., Jordano, P., Melian, C.J., Olesen, J.M., 2003. The nested assembly of plant-animal mutualistic networks. PNAS 100, 9383–9387. https://doi.org/10.1073/pnas.1633576100
