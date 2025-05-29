```
P(r̄::AbstractCoordinate, t::Time, model::JefimenkoModel; rtol=sqrt(eps))
```

空間-時間点（`r̄`,`t`）で観測される予測されたポインティングベクトル 𝐏 を、特定の `model` に対する電気および磁気のジェフェメンコ方程式を使用して計算します。指定された `relative tolerance` を使用して積分を計算します。

# 引数

  * `r̄::UnitfulCoordinateSystems.AbstractCoordinate`: 観測点の空間的位置
  * `t::Unitful.Time`: フィールドが観測される時間
  * `model::JefimenkoModel`: 送信源および伝播媒体のモデル

# キーワード

  * `rtol::Real`: 積分を解くための相対許容誤差（オプション）
