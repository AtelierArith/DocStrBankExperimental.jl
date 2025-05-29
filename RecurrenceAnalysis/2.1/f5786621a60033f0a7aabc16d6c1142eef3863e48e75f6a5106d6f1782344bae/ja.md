```
rna(R::AbstractRecurrenceMatrix)
rna(args...; kwargs...)
```

再帰ネットワークパラメータのセットを計算します。入力 `R` は対称再帰行列で、無向複雑ネットワークの隣接行列として解釈され、リンクされた頂点は位相空間の隣接点です。

また、入力はグラフオブジェクトまたは [Graphs](https://github.com/JuliaGraphs/Graphs.jl) パッケージの `SimpleGraph` コンストラクタに対する有効な入力であることもできます。

## 返り値

返される値は、以下のエントリを含む辞書で、対応するグローバルネットワーク特性[1, 2]を示します：

  * `:density`: エッジ密度、位相空間におけるグローバル再帰率にほぼ相当します。
  * `:transitivity`: ネットワークの推移性で、バラットとヴァイトの定式化[3]に従った点のグローバルクラスタリングを説明します。
  * `:averagepath`: 接続された頂点のすべてのペアにわたる最短経路長の平均値で、位相内の点の平均的な分離に関連しています。
  * `:diameter`: 接続された頂点のペア間の最短経路長の最大値で、位相空間の直径に関連しています。

## 参考文献

[1]: R.V. Donner *et al.* "Recurrence networks — a novel paradigm for nonlinear time series analysis", *New Journal of Physics* 12, 033025 (2010) [DOI:10.1088/1367-2630/12/3/033025](https://doi.org/10.1088/1367-2630/12/3/033025)

[2]: R.V. Donner *et al.*, The geometry of chaotic dynamics — a complex network perspective, *Eur. Phys. J.* B 84, 653–672 (2011) [DOI:10.1140/epjb/e2011-10899-1](https://doi.org/10.1140/epjb/e2011-10899-1)

[3]: A. Barrat & M. Weight, "On the properties of small-world network models", *The European Physical Journal B* 13, 547–560 (2000) [DOI:10.1007/s100510050067](https://doi.org/10.1007/s100510050067)
