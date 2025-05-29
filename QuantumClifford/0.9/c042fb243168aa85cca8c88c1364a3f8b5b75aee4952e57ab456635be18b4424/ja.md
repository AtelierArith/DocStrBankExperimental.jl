```julia
PauliFrame(
    frames,
    qubits,
    measurements
) -> QuantumClifford.PauliFrame{QuantumClifford.Stabilizer{QuantumClifford.Tableau{Vector{UInt8}, LinearAlgebra.Adjoint{UInt64, Matrix{UInt64}}}}}

```

与えられた数の `frames` と `qubits` を持つ空のパウリフレームのセットを準備します。`measurement` の数の測定のためのスペースを事前に確保します。
