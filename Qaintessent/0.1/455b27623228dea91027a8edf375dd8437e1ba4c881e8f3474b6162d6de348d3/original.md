```
apply(ψ::Statevector, cgs::Vector{<:CircuitGate})
```

Apply a sequence of [`CircuitGate`](@ref)(s) to a quantum state vector `ψ`.

# Examples

```jldoctest
julia> cgs = [circuit_gate(1, HadamardGate()),
                circuit_gate(1, X),
                circuit_gate(1, Y)];
julia> ψ = Statevector(ComplexF64[1 0]);
julia> apply!(ψ, cgs)
julia> ψ.state
2-element Array{Complex{Float64},1}:
 0.0 - 0.7071067811865475im
 0.0 + 0.7071067811865475im
```
