counterTrigger_sourceChannel!(rp::RedPitaya, sourceChannel::) //TODO

カウンタートリガのソースチャネルを `sourceChannel` に設定します。

# 例

```julia
julia> counterTrigger_sourceChannel!(rp, COUNTER_TRIGGER_ADC)

julia>counterTrigger_sourceChannel(rp)
COUNTER_TRIGGER_ADC::CounterTriggerSourceType = 1 //TODO
```
