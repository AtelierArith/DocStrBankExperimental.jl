```
retrieval_probs(actr::AbstractACTR, cur_time; request...)
```

各チャンクの取得リクエストに一致する取得確率を計算します。

# 引数

  * `actr::AbstractACTR`: actrオブジェクト
  * `cur_time`: 現在のシミュレーション時間（秒）

# キーワード

  * `request...`: 取得リクエストを表すオプションのキーワードペア
