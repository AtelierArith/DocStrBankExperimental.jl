```
fit!(m::LinearMixedModel; progress::Bool=true, REML::Bool=m.optsum.REML,
                          σ::Union{Real, Nothing}=m.optsum.sigma,
                          thin::Int=typemax(Int),
                          fitlog::Bool=true)
```

`LinearMixedModel`の目的関数を最適化します。`progress`が`true`の場合、目的関数の最適化中に`ProgressMeter.ProgressUnknown`の表示が表示されます。最適化に1秒以上かかる場合です。

`thin`引数は無視されます：最終的なモデルフィットには影響を与えず、`fitlog`のスリム化に関するロジックは、わずかなパフォーマンス向上のために不必要に複雑でした。
