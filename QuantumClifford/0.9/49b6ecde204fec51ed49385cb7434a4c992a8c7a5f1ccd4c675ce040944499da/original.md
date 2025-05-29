```julia
traceout!(
    s::QuantumClifford.Stabilizer,
    qubits;
    phases,
    rank
) -> Union{Tuple{QuantumClifford.Stabilizer, Int64}, QuantumClifford.Stabilizer}

```

Trace out a qubit.

See also: [`delete_columns`](@ref)
