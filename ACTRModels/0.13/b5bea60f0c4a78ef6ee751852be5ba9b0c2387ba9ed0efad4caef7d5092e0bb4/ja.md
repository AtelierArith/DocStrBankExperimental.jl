```
compute_activation!(actr, chunk::AbstractChunk; request...)
```

チャンクの活性化を計算します。デフォルトでは、現在の時間は `get_time` を使用して計算されます。

# 引数

  * `actr`: actr オブジェクト
  * `chunk::AbstractChunk`: チャンク。

# キーワード

  * `request...`: 取得リクエストのためのオプションキーワード
