```
encode!(actr, chunk, args...; kwargs...)
```

チャンクの作成を完了し、結果として得られた `chunk` をイマジナルバッファに追加します。バッファの状態は busy = false および empty = false に設定されます。

# 引数

  * `actr`: ACT-R モデルオブジェクト
  * `chunk`: メモリチャンク
