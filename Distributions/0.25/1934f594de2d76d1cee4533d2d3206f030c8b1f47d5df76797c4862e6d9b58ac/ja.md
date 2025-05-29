```
DiscreteNonParametric(xs, ps)
```

*離散非パラメトリック分布*は、実数のサポート値のリストとそれに対応する確率を用いて、任意の確率質量関数を明示的に定義します。

```julia
d = DiscreteNonParametric(xs, ps)

params(d)  # パラメータを取得します。すなわち (xs, ps)
support(d) # 分布のサポート (xs) を記述するソートされた AbstractVector を取得します
probs(d)   # サポートに関連する確率 (ps) のベクトルを取得します
```

外部リンク

  * [確率質量関数 - Wikipedia](http://en.wikipedia.org/wiki/Probability_mass_function)
