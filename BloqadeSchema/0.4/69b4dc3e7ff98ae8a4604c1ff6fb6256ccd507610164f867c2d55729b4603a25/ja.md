```
function to_braket_ahs_ir(amplitude_or_phase::Union{BloqadeSchema.RabiFrequencyAmplitude,
BloqadeSchema.RabiFrequencyPhase})
```

`amplitude_or_phase`を展開して、その`global_value`フィールドを抽出し、`function to_braket_ahs_ir(global_values::BloqadeSchema.GlobalField)`によって即座に評価されます。
