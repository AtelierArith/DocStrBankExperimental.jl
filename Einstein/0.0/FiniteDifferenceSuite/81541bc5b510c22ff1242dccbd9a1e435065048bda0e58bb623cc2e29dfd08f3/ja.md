```
fdm_boundary_weights([TR=Rational{TI}], derivative_order::TI, accuracy_order::TI) where {TR<:Real, TI<:Integer}
```

シフト境界条件の有限差分係数を生成します。

# 引数

  * `derivative_order::Integer`: 近似する導関数の次数
  * `accuracy_order::Integer`: 希望する精度の次数

# 戻り値

左および右のシフト境界有限差分係数のタプル。係数は行列に格納され、行は異なるグリッドポイントを表します。行は最も左のグリッドポイントから最も右のグリッドポイントまでの順に並んでいます。
