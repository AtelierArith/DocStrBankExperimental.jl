```
mix(x::AbstractSampler, y::AbstractSampler, t::AbstractSampler)
```

サンプラー `x` と `y` の出力をサンプラー `t` の出力によって線形補間した結果を出力する修飾サンプラーを構築します。
