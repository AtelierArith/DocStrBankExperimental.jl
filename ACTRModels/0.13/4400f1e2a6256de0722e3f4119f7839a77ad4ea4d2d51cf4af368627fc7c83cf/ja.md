```
compute_activation!(actr::AbstractACTR, chunks::Vector{<:Chunk}; request...)
```

チャンクのベクトルの活性化を計算します。デフォルトでは、現在の時間は `get_time` で計算されます。

# 引数

  * `actr::AbstractACTR`: `ACTR` オブジェクト
  * `chunks::Vector{<:Chunk}`: チャンクのベクトル。

# キーワード

  * `request...`: 取得リクエストのためのオプションのキーワード
