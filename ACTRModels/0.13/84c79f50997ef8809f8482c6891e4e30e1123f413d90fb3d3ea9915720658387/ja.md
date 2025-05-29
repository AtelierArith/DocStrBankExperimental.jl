```
retrieval_prob(actr::AbstractACTR, chunk::AbstractChunk; request...)
```

ソフトマックス近似を使用して、チャンクを取得するための取得確率を計算します。デフォルトでは、現在の時間は `get_time` から計算されます。

# 引数

  * `actr::AbstractACTR`: ACT-R オブジェクト
  * `chunk::AbstractChunk`: チャンク

# キーワード

  * `request...`: 取得リクエストを表すオプションのキーワードペア
