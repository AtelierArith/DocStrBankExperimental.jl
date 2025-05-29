counterTrigger_sourceChannel(rp::RedPitaya)

Get the source channel of the counter trigger.

# Example

```julia
julia> counterTrigger_sourceChannel!(rp, COUNTER_TRIGGER_IN2)

julia>counterTrigger_sourceChannel(rp)
COUNTER_TRIGGER_IN2::CounterTriggerSourceADCChannel = 2
```
