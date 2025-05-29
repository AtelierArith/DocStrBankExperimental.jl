```
retrieve(actr::AbstractACTR, cur_time; request...)
```

取得リクエストに基づいてチャンクを取得します

# 引数

  * `actr::AbstractACTR`: ACT-Rオブジェクト
  * `cur_time`: 現在のシミュレーション時間（秒）

# キーワード

  * `request...`: 取得リクエストを表すオプションのキーワード引数、例: person=:bob
