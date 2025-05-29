```
compute_activation!(actr::AbstractACTR, cur_time::Float64; request...)
```

宣言的記憶内のすべてのチャンクの活性化を計算します

# 引数

  * `actr::AbstractACTR`: `ACTR`オブジェクト
  * `cur_time`: 現在のシミュレーション時間（秒）

# キーワード

  * `request...`: 取得リクエストのためのオプションキーワード
