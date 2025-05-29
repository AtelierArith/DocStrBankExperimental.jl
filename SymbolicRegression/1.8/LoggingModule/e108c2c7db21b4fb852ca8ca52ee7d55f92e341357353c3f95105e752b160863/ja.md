```
SRLogger(logger::AbstractLogger; log_interval::Int=100)
```

別のロガーをラップするシンボリック回帰用のロガーです。

# 引数

  * `logger`: ラップする基本ロガー
  * `log_interval`: ロギングイベントの間のステップ数。デフォルトは100（100ステップごとにログを記録）。
