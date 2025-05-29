```
counterTrigger_referenceCounter(rp::RedPitaya)
```

カウンタートリガーがトリガーすべきカウンタ値を返します。

# 例

```julia
julia> counterTrigger_referenceCounter!(rp, 250)
true

julia> counterTrigger_referenceCounter(rp)
250
```
