counterTrigger_referenceCounter!(rp::RedPitaya, presamples)

カウンタートリガーがトリガーすべきサンプル数を設定します。

# 例

```julia
julia> counterTrigger_referenceCounter(rp, 250)
true

julia> counterTrigger_referenceCounter!(rp)
250
```
