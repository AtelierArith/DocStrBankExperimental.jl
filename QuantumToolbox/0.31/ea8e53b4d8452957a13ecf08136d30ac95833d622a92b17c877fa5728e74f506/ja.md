```
expect(O::Union{AbstractQuantumObject,Vector{AbstractQuantumObject}}, ψ::Union{QuantumObject,Vector{QuantumObject}})
```

演算子 [`Operator`](@ref) `O` の期待値を状態 `ψ` で計算します。状態は [`Ket`](@ref)、[`Bra`](@ref)、または [`Operator`](@ref) であることができます。

もし `ψ` が [`Ket`](@ref) または [`Bra`](@ref) の場合、関数は $\langle\psi|\hat{O}|\psi\rangle$ を計算します。

もし `ψ` が密度行列（[`Operator`](@ref)）の場合、関数は $\textrm{Tr} \left[ \hat{O} \hat{\psi} \right]$ を計算します。

関数は、`O` が `Hermitian` 型または `Symmetric` 型の場合は実数を返し、それ以外の場合は複素数を返します。演算子 `O` をエルミートにするには `Hermitian(O)` を使用します。

!!! note "観測量と状態のリスト"
    観測量 `O` と状態 `ψ` は [`QuantumObject`](@ref) のリストとして与えることができ、期待値のリストを返します。両方がリストとして与えられた場合、期待値の `Matrix` を返します。


# 例

```jldoctest
julia> ψ1 = 1 / √2 * (fock(10,2) + fock(10,4));

julia> ψ2 = coherent(10, 0.6 + 0.8im);

julia> a = destroy(10);

julia> expect(a' * a, ψ1) |> round
3.0 + 0.0im

julia> expect(Hermitian(a' * a), ψ1) |> round
3.0

julia> round.(expect([a' * a, a' + a, a], [ψ1, ψ2]), digits = 1)
3×2 Matrix{ComplexF64}:
 3.0+0.0im  1.0+0.0im
 0.0+0.0im  1.2-0.0im
 0.0+0.0im  0.6+0.8im
```
