```
retrieval_prob(actr::AbstractACTR, chunk::AbstractChunk, cur_time=0.0; request...)
```

チャンクを取得するための取得確率を計算するためにソフトマックス近似を使用します。

# 引数

  * `actr::AbstractACTR`: ACT-Rオブジェクト
  * `chunk::AbstractChunk`: チャンク
  * `cur_time`: 現在のシミュレーション時間（秒）

# キーワード

  * `request...`: 取得リクエストを表すオプションのキーワードペア
