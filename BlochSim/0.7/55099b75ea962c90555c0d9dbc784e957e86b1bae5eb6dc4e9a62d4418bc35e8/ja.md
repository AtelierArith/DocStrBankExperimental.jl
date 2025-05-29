```
GradientSpoiling(grad, Tg) <: AbstractSpoiling
GradientSpoiling(gx, gy, gz, Tg)
```

勾配スプーリングを表します。例えば、時間 `Tg` (ms) のために勾配 `grad = Gradient(gx, gy, gz)` を適用します。`grad` は `Gradient` であるか、`gx`、`gy`、および `gz` がスカラーである場合、定数勾配を表します。また、`grad` は `Gradient` のコレクションであるか、`gx`、`gy`、および `gz` が値のコレクションである場合、定数時間ステップを持つ勾配波形を表します。
