```
compute_activation!(actr::AbstractACTR; request...)
```

宣言的記憶内のすべてのチャンクの活性化を計算します。デフォルトでは、現在の時間は `get_time` を使用して計算されます。

# 引数

  * `actr::AbstractACTR`: `ACTR` オブジェクト

# キーワード

  * `request...`: 取得リクエストのためのオプションのキーワード
