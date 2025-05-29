```
nodeflux(system, F,U; data)
```

三角形分割のノード上でのベクトル関数としてのエッジ関数の再構成。結果は、フラックス密度を示す離散化ノードによって張られたFEM空間における区分線形ベクトル関数として見ることができます。

再構成は、"魔法の公式" R. Eymard, T. Gallouët, R. Herbin, IMA Journal of Numerical Analysis (2006) 26, 326−353, Lemma 2.4 に基づいています（または: [hal.science/hal-00004840](https://hal.science/hal-00004840)）。

戻り値は `dim x nspec x nnodes` のベクトルです。

注意: コード内のドメインコーナーでの値に関して未解決の問題がある可能性があります。この問題の現れとして、潜在的な境界アーティファクトを確認し、報告してください。
