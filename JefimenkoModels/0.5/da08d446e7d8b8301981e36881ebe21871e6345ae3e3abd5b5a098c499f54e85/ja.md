```
H(r̄::AbstractCoordinate, t::Time, model::JefimenkoModel; rtol=sqrt(eps))
```

特定の `model` に対して、磁気ジェフェメンコ方程式を使用して、時空間点（`r̄`,`t`）で観測される予測された磁場 𝐇 を計算します。指定された `relative tolerance` を使用して積分を計算します。

# 引数

  * `r̄::UnitfulCoordinateSystems.AbstractCoordinate`: 観測点の空間的位置
  * `t::Unitful.Time`: 磁場が観測される時刻
  * `model::JefimenkoModel`: 送信源と伝播媒体のモデル

# キーワード

  * `rtol::Real`: 積分を解くための相対許容誤差（オプション）
