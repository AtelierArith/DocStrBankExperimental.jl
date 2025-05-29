```
function to_braket_ahs_ir(detuning::BloqadeSchema.Detuning)
```

`detuning`を`Braket.IR.PhysicalField`の`global_value`および`local_value`フィールドに変換します。変換された`global_value`を最初に返し、その後に`local_value`を返します。``
