```
delay!(clk, Δt)
delay!(clk, T, t)
```

プロセスをクロック `clk` で時間間隔 `Δt` だけ遅延（停止）させます。

# 引数

  * `clk::Clock`,
  * `Δt`: 時間間隔、`Number` または `Distribution`,
  * `T::Timing`: `until` のみが受け入れられます,
  * `t`: 時間遅延、`Number` または `Distribution`.
