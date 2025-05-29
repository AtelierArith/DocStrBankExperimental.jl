```
state(::AbstractSite, ::String)
```

指定されたサイトと名前に対応するローカル状態（ベクトルまたは行列）を返します

# 例

```jldoctest
julia> using TensorMixedStates, .Qubits, .Fermions

julia> state(Qubit(), "+")
2-element Vector{Float64}:
 0.7071067811865475
 0.7071067811865475

julia> state(Fermion(), "FullyMixed")
2×2 Matrix{Float64}:
 0.5  0.0
 0.0  0.5
```
