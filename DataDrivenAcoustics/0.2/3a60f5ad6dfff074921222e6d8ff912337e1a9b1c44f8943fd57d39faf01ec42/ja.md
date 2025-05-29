```julia
transfercoef(model, tx, rx; mode)

```

位置 `rx` での伝送係数をデータ駆動型物理ベースの伝播モデルを使用して計算します。

  * `model`: データ駆動型物理ベースの伝播モデル
  * `tx`: 音源。これはオプションです。未知の音源には `missing` または `nothing` を使用します。
  * `rx`: 音受信機の位置
