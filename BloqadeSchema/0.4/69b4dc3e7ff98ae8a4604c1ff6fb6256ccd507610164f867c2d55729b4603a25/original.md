```
function to_braket_ahs_ir(amplitude_or_phase::Union{BloqadeSchema.RabiFrequencyAmplitude,
BloqadeSchema.RabiFrequencyPhase})
```

Unwraps `amplitude_or_phase` to extract their `global_value` fields which are  immediately evaluated by `function to_braket_ahs_ir(global_values::BloqadeSchema.GlobalField)`
