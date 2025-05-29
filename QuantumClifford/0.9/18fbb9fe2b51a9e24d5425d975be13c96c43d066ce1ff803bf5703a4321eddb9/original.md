```julia
reset_qubits!(
    s::QuantumClifford.Stabilizer,
    newstate,
    qubits;
    phases
) -> Union{QuantumClifford.PauliOperator, QuantumClifford.Stabilizer}

```

Reset a given set of qubits to be in the state `newstate`. These qubits are traced out first, which could lead to "nonlocal" changes in the tableau.
