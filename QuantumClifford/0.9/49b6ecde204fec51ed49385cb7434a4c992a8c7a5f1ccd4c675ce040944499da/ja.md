```julia
traceout!(
    s::QuantumClifford.Stabilizer,
    qubits;
    phases,
    rank
) -> Union{Tuple{QuantumClifford.Stabilizer, Int64}, QuantumClifford.Stabilizer}

```

キュービットをトレースアウトします。

関連情報: [`delete_columns`](@ref)
