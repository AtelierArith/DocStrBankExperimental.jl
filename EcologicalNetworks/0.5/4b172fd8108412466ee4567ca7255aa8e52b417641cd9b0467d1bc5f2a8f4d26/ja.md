```
null3(N::BinaryNetwork; dims::Integer=1)
```

ネットワーク `N` が与えられた場合、`null3(N)` は同じ次元の行列を返します。この行列では、すべての相互作用が各種の出次数（`dims=1`）または入次数（`dims=2`、前駆者の数）に等しい確率で発生し、可能な前駆者/後継者の総数で割られます。

この分析の出力は、ネットワークが退化していないことを保証するものではないため、出力は `is_degenerate` を使用してフィルタリングするか、`simplify` に渡すべきです。このアプローチの出力は、元のネットワークと同じ部分性を持つ確率的ネットワークであることが *常に* です。

#### 参考文献

Poisot, T., Stanko, M., Miklisová, D., Morand, S., 2013. Facultative and obligate parasite communities exhibit different network properties. Parasitology 140, 1340–1345. https://doi.org/10.1017/S0031182013000851
