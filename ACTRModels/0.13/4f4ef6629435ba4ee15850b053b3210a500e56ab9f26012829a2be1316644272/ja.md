```
retrieval_prob(actr::AbstractACTR, target::Array{<:Chunk,1}; request...)
```

ソフトマックス近似を使用して、チャンクを取得する確率を計算します。デフォルトでは、現在の時間は `get_time` から計算されます。

# 引数

  * `actr::AbstractACTR`: ACT-R オブジェクト
  * `target::Array{<:Chunk,1}`: ソフトマックス関数の分子にあるチャンクのベクトル

# キーワード

  * `request...`: 取得リクエストを表すオプションのキーワードペア
