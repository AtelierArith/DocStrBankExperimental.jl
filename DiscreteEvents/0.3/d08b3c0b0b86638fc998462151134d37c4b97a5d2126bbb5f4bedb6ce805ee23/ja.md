```
sample_time!([clk::Clock], Δt::N) where {N<:Number}
```

現在から時計のサンプルレートを設定します（`tau(clk)`）。

# 引数

  * `clk::Clock`: 指定されていない場合、𝐶のサンプルレートを設定します。
  * `Δt::N`: サンプルレート、サンプリングの時間間隔
