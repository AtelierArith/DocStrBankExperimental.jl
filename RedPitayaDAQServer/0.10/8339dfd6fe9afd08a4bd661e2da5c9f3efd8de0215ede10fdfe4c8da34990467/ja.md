```
counterTrigger_presamples!(rp::RedPitaya, presamples)
```

カウンタートリガーがリファレンスカウンターに到達する前にトリガーすべきサンプル数を設定します。

# 例

```julia
julia> counterTrigger_presamples!(rp, 50)
true

julia> counterTrigger_presamples(rp)
50
```
