```julia
pftrajectories(
    register::QuantumClifford.Register,
    circuit;
    trajectories
) -> Tuple{QuantumClifford.Register, QuantumClifford.PauliFrame{QuantumClifford.Stabilizer{QuantumClifford.Tableau{Vector{UInt8}, LinearAlgebra.Adjoint{UInt64, Matrix{UInt64}}}}, Matrix{Bool}}}

```

与えられた [`Register`](@ref) と回路に対して、レジスタに作用する参照回路をシミュレートし、その後、数多くの [`PauliFrame`](@ref) 軌道もシミュレートします。レジスタと [`PauliFrame`](@ref) インスタンスを返します。

測定結果を取得するには [`pfmeasurements`](@ref) を使用してください。
