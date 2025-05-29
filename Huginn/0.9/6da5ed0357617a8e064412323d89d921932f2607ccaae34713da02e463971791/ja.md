```
halfar_solution(R, t, h₀, r₀, A, n, physical_parameters::PhysicalParameters)
```

SIA方程式のHalfar解の評価を返します。

引数:

  * `R`: 放射距離。解は原点の中心を中心に極対称性を持ちます。
  * `t`: 時間。
  * `h₀`および`r₀`: Halfar解のパラメータ。
  * `A`: グレンの法則のパラメータ。
  * `n`: クリープ指数。
  * `physical_parameters::PhysicalParameters`: 氷の密度と重力定数を取得するための物理パラメータ。
