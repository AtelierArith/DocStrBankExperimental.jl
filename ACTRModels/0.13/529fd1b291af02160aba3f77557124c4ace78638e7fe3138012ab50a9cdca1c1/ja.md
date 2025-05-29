```
add_chunk!(actr::AbstractACTR; slots...)
```

宣言的記憶に新しいチャンクを追加するか、新しい使用法で既存のチャンクを更新します。デフォルトの時間は `get_time` から計算されます。

# 引数

  * `actr::AbstractACTR`: ACT-R モデルオブジェクト

# キーワード

  * `slots...`: スロット-値ペアに対応するオプションのキーワード引数、例: name=:Bob
