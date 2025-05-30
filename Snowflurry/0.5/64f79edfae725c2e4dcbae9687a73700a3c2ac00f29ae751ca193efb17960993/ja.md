ブラ（すなわち、複素値の行ベクトル）を表す構造体。ブラはケトの複素共役として作成されます。

# 例

```jldoctest
julia> ψ = fock(1, 3)
3-element Ket{ComplexF64}:
0.0 + 0.0im
1.0 + 0.0im
0.0 + 0.0im


julia> _ψ = Bra(ψ)
3-element Bra{ComplexF64}:
0.0 - 0.0im
1.0 - 0.0im
0.0 - 0.0im


julia> _ψ * ψ    # ブラとケトの積はスカラー
1.0 + 0.0im

julia> ψ*_ψ     # ケトとブラの積は演算子
(3, 3)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im


```
