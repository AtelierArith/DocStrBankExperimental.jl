```
setagc(;gain=1.0, maxvalue=0.6, minstep=-0.6)
```

自動ゲイン制御モジュールのパラメータを設定します。

# オプション引数

  * `gain`: 初期音声信号のゲイン値
  * `maxvalue`: 音声信号の指定された最大値、maxvalue ∈ (0, +Inf)
  * `minstep`: ゲインを変更するための最小値、minstep ∈ (-1, 0)
