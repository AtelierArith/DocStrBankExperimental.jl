```julia
pftrajectories(
    state::QuantumClifford.PauliFrame,
    circuit
) -> QuantumClifford.PauliFrame

```

与えられた回路によって[`PauliFrame`](@ref)に保存された各フレームを進化させます。
