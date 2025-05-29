```
expected_value(A::AbstractOperator, psi::Ket)
```

演算子 `A` とケト |`ψ`⟩ に対して期待値 ⟨`ψ`|`A`|`ψ`⟩ を計算します。

# 例

```jldoctest
julia> ψ = Ket([0.0; 1.0])
2-element Ket{ComplexF64}:
0.0 + 0.0im
1.0 + 0.0im


julia> A = sigma_z()
(2,2)-element Snowflurry.DiagonalOperator:
Underlying data type: ComplexF64:
1.0 + 0.0im    .
.    -1.0 + 0.0im


julia> expected_value(A, ψ)
-1.0 + 0.0im
```
