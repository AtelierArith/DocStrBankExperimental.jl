```
norm(A::QuantumObject, p::Real)
```

標準ベクトル `p`-ノルムまたは [`QuantumObject`](@ref) の [Schatten](https://en.wikipedia.org/wiki/Schatten_norm) `p`-ノルムを `A` の型に応じて返します：

  * `A` が [`Ket`](@ref)、[`Bra`](@ref)、[`OperatorKet`](@ref)、または [`OperatorBra`](@ref) のいずれかである場合、`A` の標準ベクトル `p`-ノルム（デフォルト `p=2`）を返します。
  * `A` が [`Operator`](@ref) または [`SuperOperator`](@ref) のいずれかである場合、`A` の [Schatten](https://en.wikipedia.org/wiki/Schatten_norm) `p`-ノルム（デフォルト `p=1`）を返します。

# 例

```jldoctest
julia> ψ = fock(10, 2)

Quantum Object:   type=Ket()   dims=[10]   size=(10,)
10-element Vector{ComplexF64}:
 0.0 + 0.0im
 0.0 + 0.0im
 1.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im

julia> norm(ψ)
1.0
```
