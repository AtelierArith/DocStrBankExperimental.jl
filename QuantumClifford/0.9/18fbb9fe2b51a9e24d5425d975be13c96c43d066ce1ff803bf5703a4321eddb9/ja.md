```julia
reset_qubits!(
    s::QuantumClifford.Stabilizer,
    newstate,
    qubits;
    phases
) -> Union{QuantumClifford.PauliOperator, QuantumClifford.Stabilizer}

```

指定された量子ビットのセットを状態 `newstate` にリセットします。これらの量子ビットは最初にトレースアウトされ、これによりタブローに「非局所的」な変化が生じる可能性があります。
