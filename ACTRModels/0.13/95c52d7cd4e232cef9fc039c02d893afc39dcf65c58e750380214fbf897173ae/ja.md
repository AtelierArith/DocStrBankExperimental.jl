```
add_chunk!(actr::AbstractACTR, cur_time=0.0; slots...)
```

宣言的記憶に新しいチャンクを追加するか、新しい使用で既存のチャンクを更新します。

# 引数

  * `actr::AbstractACTR`: ACT-Rモデルオブジェクト
  * `cur_time=0.0`: 現在のシミュレーション時間（秒）

# キーワード

  * `slots...`: スロット-値ペアに対応するオプションのキーワード引数、例: name=:Bob
