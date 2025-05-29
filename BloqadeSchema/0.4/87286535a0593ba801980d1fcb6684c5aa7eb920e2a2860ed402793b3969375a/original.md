```
function to_braket_ahs_ir(detuning::BloqadeSchema.Detuning)
```

Converts `detuning` to `Braket.IR.PhysicalField`'s for the `global_value` and `local_value` fields of `detuning`. Returns the converted `global_value` first  followed by the `local_value`.  ``
