```
retrieval_prob(actr::AbstractACTR, target::Array{<:Chunk,1}, cur_time; request...)
```

指定された `target` のチャンクのセットから1つのチャンクの取得確率を計算します。取得確率はソフトマックス近似を用いて計算されます。

# 引数

  * `actr::AbstractACTR`: actrオブジェクト
  * `target::Array{<:Chunk,1}`: ソフトマックス関数の分子にあるチャンクのベクトル
  * `cur_time`: 現在の時間（秒）

# キーワード

  * `request...`: 取得リクエストのためのオプションキーワード
