```julia
arrivals(model, tx, rx; threshold)

```

位置 `rx` で到着光線をデータ駆動型物理ベースの伝播モデルを使用して表示します。

  * `model`: データ駆動型物理ベースの伝播モデル
  * `tx`: 音響源。これはオプションです。未知のソースには `missing` または `nothing` を使用します。
  * `rx`: 音響受信機
