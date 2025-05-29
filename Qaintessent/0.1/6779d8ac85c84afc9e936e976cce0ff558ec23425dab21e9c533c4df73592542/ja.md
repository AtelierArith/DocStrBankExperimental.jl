```
apply(ψ::Statevector, cg::CircuitGate{M,G}) where {M,G}
```

量子状態ベクトル `ψ` に [`CircuitGate`](@ref) を適用します。

# 例

```jldoctest
julia> cg = circuit_gate(1, HadamardGate());
julia> ψ = Statevector(ComplexF64[1 0]);
julia> apply!(ψ, cg)
julia> ψ.state
2-element Array{Complex{Float64},1}:
 0.7071067811865475 + 0.0im
 0.7071067811865475 + 0.0im
```
