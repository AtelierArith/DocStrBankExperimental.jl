```
get_measurement_probabilities(x::Ket{Complex{T}},
    [target_bodies::Vector{U},
    hspace_size_per_body::Union{U,Vector{U}}=2])::AbstractVector{T}
    where {T<:Real, U<:Integer}
```

`Ket` `x`の`target_bodies`の測定確率をリストするベクトルを返します。

各ボディのヒルベルト空間のサイズは、`hspace_size_per_body`引数に`Integer`の`Vector`を提供することで指定できます。`Vector`は各ボディのヒルベルト空間のサイズを指定する必要があります。空間のサイズが均一な場合は、単一の`Integer`を代わりに指定できます。`x`のみが提供された場合、すべてのボディの確率が提供されます。

測定確率は、最小の計算基底状態から最大の計算基底状態までリストされます。たとえば、2量子ビットの`Ket`の場合、確率は$\left|00\right\rangle$、$\left|10\right\rangle$、$\left|01\right\rangle$、および$\left|11\right\rangle$の順にリストされます。

!!! note
    規約として、量子ビット1は最も左のビットであり、その後に続くすべての量子ビットがあります。$\left|10\right\rangle$は、量子ビット1が状態$\left|1\right\rangle$で、量子ビット2が状態$\left|0\right\rangle$にあります。


# 例

次の例では、測定する確率が$\left|00\right\rangle$で50%、$\left|01\right\rangle$でも50%の`Ket`を構築します。

```jldoctest get_measurement_probabilities
julia> ψ = 1/sqrt(2) * Ket([1, 0, 1, 0])
4-element Ket{ComplexF64}:
0.7071067811865475 + 0.0im
0.0 + 0.0im
0.7071067811865475 + 0.0im
0.0 + 0.0im


julia> get_measurement_probabilities(ψ)
4-element Vector{Float64}:
 0.4999999999999999
 0.0
 0.4999999999999999
 0.0

```

同じ`Ket`に対して、量子ビット2を測定して0を見つける確率は100%です。

```jldoctest get_measurement_probabilities
julia> target_qubit = [2];

julia> get_measurement_probabilities(ψ, target_qubit)
2-element Vector{Float64}:
 0.9999999999999998
 0.0

```
