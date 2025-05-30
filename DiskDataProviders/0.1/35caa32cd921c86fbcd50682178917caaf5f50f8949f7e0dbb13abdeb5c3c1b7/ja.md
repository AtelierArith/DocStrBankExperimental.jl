```
ChannelDiskDataProvider{XT, YT}(xsize, batchsize, queuelength::Int; kwargs...) where {XT, YT}
```

ChannelDiskDataProviderのコンストラクタ。`{XT, YT}`はそれぞれ入力と出力の型です。

# 引数:

  * `xsize`: 各データポイントのサイズを持つタプル
  * `batchsize`: バッチに入れるデータポイントの数
  * `queuelength`: バッファの長さ。これをバッチサイズの整数倍にするのが良いアイデアです。
  * `kwargs`: 構造体の他のフィールドを設定するため。
  * `transform`: データポイントをバッチに入れる前に変換する関数 `(x,y)->(x,y)` または `x->x`。これを使用して、例えば、前処理や正規化などを適用できます。
