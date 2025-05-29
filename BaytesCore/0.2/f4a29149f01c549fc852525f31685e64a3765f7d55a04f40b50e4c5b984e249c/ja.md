```julia
struct ResampleTune{R<:BaytesCore.ResamplingMethod}
```

リサンプリングステップに関する情報を格納します。

# フィールド

  * `method::BaytesCore.ResamplingMethod`: リサンプリングの方法。
  * `update::BaytesCore.Updater`: 最後のイテレーションがリサンプリングされたかどうかを格納します。
