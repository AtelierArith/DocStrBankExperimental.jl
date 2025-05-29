```
timeline(;t_start::Real=0., t_end::Real, step::Real=(t_end - t_start)/250.)
```

キーワードに基づいて、時間データのみを持つ `RheoTimeData` 構造体を生成します。

# 引数

  * `t_start`: 開始時間、通常は 0
  * `t_end`: 終了時間
  * `step`: サンプル間の時間。デフォルトは約 250 の時間ポイントを提供するように設定されています。
