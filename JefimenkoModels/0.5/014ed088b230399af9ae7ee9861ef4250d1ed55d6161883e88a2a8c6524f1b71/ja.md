```
H(r̄::AbstractCoordinate, t::Time, model::JefimenkoModel; rtol=sqrt(eps))
```

特定の `model` に対して、電気的ジェフィメンコ方程式を使用して、時空間点（`r̄`,`t`）で観測される予測電場 𝐇 を計算します。指定された相対許容誤差を使用して積分を計算します。

# 引数

  * `r̄::UnitfulCoordinateSystems.AbstractCoordinate`: 観測点の空間位置
  * `t::Unitful.Time`: 電場が観測される時刻
  * `model::JefimenkoModel`: 送信源と伝播媒体のモデル

# キーワード

  * `rtol::Real`: 積分を解く際の相対許容誤差（オプション）
