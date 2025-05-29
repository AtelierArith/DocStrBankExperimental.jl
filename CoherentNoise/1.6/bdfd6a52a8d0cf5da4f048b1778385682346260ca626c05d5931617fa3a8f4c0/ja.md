```
mix(x::AbstractSampler, y::AbstractSampler, t::Real)
```

サンプラー `x` と `y` の出力をスカラー `t` によって線形補間した結果を出力する修飾子サンプラーを構築します。
