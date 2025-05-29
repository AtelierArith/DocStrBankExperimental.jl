```
counterTrigger_sourceType!(rp::RedPitaya, sourceType::CounterTriggerSourceType)
```

カウンタートリガーのソースタイプを `sourceType` に設定します。

# 例

```julia
julia> counterTrigger_sourceType!(rp, COUNTER_TRIGGER_ADC)

julia>counterTrigger_sourceType(rp)
COUNTER_TRIGGER_ADC::CounterTriggerSourceType = 1
```
