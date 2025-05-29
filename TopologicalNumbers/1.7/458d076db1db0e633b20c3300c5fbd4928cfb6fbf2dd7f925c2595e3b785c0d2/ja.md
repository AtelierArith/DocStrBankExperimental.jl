```
WCSSolution{T1,T2,T3} <: TopologicalNumbersSolutions
```

`WCSSolution`構造体は、ワイル点を見つけて計算するための解を表します。

# フィールド

  * `kn::T1`: ブリルアンゾーンの`"kn"`方向に垂直な平面のチェルン数を計算します（`"k1"`、`"k2"`、`"k3"`）。
  * `param::T2`: `"kn"`方向の波数パラメータ。
  * `nums::T3`: 各エネルギーバンドおよび各波数パラメータのチェルン数。
