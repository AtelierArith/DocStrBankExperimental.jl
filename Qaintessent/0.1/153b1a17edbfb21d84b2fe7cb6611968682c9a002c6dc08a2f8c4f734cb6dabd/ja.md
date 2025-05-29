```
apply(ψ::Vector{<:Complex}, cgs::Vector{<:CircuitGate})
```

量子状態ベクトル `ψ` に一連の [`CircuitGate`](@ref)(s) を適用します。

# 例

```jldoctest
julia> cgs = [circuit_gate(1, HadamardGate()),
                circuit_gate(1, X),
                circuit_gate(1, Y)];
julia> ψ = [1 0];
julia> apply(ψ, cgs)
2-element Array{Complex{Float64},1}:
 0.0 - 0.7071067811865475im
 0.0 + 0.7071067811865475im
```
