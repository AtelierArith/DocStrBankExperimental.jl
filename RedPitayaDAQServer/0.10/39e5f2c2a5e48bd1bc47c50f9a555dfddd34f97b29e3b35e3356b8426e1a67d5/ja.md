counterTrigger_sourceChannel(rp::RedPitaya)

カウンタートリガのソースチャネルを取得します。

# 例

```julia
julia> counterTrigger_sourceChannel!(rp, COUNTER_TRIGGER_IN2)

julia>counterTrigger_sourceChannel(rp)
COUNTER_TRIGGER_IN2::CounterTriggerSourceADCChannel = 2
```
