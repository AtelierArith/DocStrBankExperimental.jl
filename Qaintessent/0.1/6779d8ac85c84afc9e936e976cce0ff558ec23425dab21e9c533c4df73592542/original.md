```
apply(ψ::Statevector, cg::CircuitGate{M,G}) where {M,G}
```

Apply a [`CircuitGate`](@ref) to a quantum state vector `ψ`.

# Examples

```jldoctest
julia> cg = circuit_gate(1, HadamardGate());
julia> ψ = Statevector(ComplexF64[1 0]);
julia> apply!(ψ, cg)
julia> ψ.state
2-element Array{Complex{Float64},1}:
 0.7071067811865475 + 0.0im
 0.7071067811865475 + 0.0im
```
