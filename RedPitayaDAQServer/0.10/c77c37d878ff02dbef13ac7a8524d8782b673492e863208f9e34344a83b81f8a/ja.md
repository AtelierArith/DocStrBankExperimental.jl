```
counterTrigger_sourceType(rp::RedPitaya)
```

カウンタートリガのソースタイプを取得します。

# 例

```julia
julia> counterTrigger_sourceType!(rp, COUNTER_TRIGGER_ADC)

julia>counterTrigger_sourceType(rp)
COUNTER_TRIGGER_ADC::CounterTriggerSourceType = 1
```
