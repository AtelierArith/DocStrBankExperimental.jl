counterTrigger_sourceChannel!(rp::RedPitaya, sourceChannel::) //TODO

Set the source channel of the counter trigger to `sourceChannel`.

# Example

```julia
julia> counterTrigger_sourceChannel!(rp, COUNTER_TRIGGER_ADC)

julia>counterTrigger_sourceChannel(rp)
COUNTER_TRIGGER_ADC::CounterTriggerSourceType = 1 //TODO
```
