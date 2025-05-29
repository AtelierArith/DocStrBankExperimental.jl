```
compute_activation!(actr::AbstractACTR, chunks::Vector{<:Chunk}, cur_time::Float64; request...)
```

チャンクのベクトルの活性化を計算します

# 引数

  * `actr::AbstractACTR`: `ACTR`オブジェクト
  * `chunks::Vector{<:Chunk}`: チャンクのベクトル。
  * `cur_time::Float64`: 現在のシミュレーション時間（秒）

# キーワード

  * `request...`: 取得リクエストのためのオプションキーワード
