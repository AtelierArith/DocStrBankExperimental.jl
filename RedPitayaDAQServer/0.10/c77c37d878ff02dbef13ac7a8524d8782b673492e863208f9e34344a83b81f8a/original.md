```
counterTrigger_sourceType(rp::RedPitaya)
```

Get the source type of the counter trigger.

# Example

```julia
julia> counterTrigger_sourceType!(rp, COUNTER_TRIGGER_ADC)

julia>counterTrigger_sourceType(rp)
COUNTER_TRIGGER_ADC::CounterTriggerSourceType = 1
```
