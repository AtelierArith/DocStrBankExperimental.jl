```
agc!(wav::Array, fs::Real=16000.0; maxvalue::Real=0.6, minstep::Real=-0.6)
```

音声信号の自動ゲイン制御モジュール。この関数を呼び出した後、入力信号 `wav` は変更されます。

# 引数

  * `wav`: 生の音声信号
  * `fs`: サンプリングレート
  * `maxvalue`: 音声信号の指定された最大値、maxvalue ∈ (0, +Inf)
  * `minstep`: ゲインを変更するための最小値、minstep ∈ (-1, 0)
