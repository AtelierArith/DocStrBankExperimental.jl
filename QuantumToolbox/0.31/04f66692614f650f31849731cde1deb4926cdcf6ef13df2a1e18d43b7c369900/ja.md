```
ptrace(QO::QuantumObject, sel)
```

量子状態 `QO` の[部分トレース](https://en.wikipedia.org/wiki/Partial_trace)で、`sel` ベクトルに存在するインデックスを持つ次元のみを残します。

この関数は常に [`Operator`](@ref) を返すことに注意してください。入力が [`QuantumObject`](@ref) であっても、それが [`Ket`](@ref)、[`Bra`](@ref)、または [`Operator`](@ref) であっても関係ありません。

# 例

状態 $\ket{\psi} = \ket{e,g}$ の二つのキュービット:

```jldoctest
julia> ψ = kron(fock(2,0), fock(2,1))

Quantum Object:   type=Ket()   dims=[2, 2]   size=(4,)
4-element Vector{ComplexF64}:
 0.0 + 0.0im
 1.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im

julia> ptrace(ψ, 2)

Quantum Object:   type=Operator()   dims=[2]   size=(2, 2)   ishermitian=true
2×2 Matrix{ComplexF64}:
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  1.0+0.0im
```

または、エンタングル状態 $\ket{\psi} = \frac{1}{\sqrt{2}} \left( \ket{e,e} + \ket{g,g} \right)$ の場合:

```jldoctest
julia> ψ = 1 / √2 * (kron(fock(2,0), fock(2,0)) + kron(fock(2,1), fock(2,1)))

Quantum Object:   type=Ket()   dims=[2, 2]   size=(4,)
4-element Vector{ComplexF64}:
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
 0.7071067811865475 + 0.0im

julia> ptrace(ψ, 1)

Quantum Object:   type=Operator()   dims=[2]   size=(2, 2)   ishermitian=true
2×2 Matrix{ComplexF64}:
 0.5+0.0im  0.0+0.0im
 0.0+0.0im  0.5+0.0im
```
