```
expected_value(A::AbstractOperator, psi::Ket)
```

Compute the expectation value ⟨`ψ`|`A`|`ψ`⟩ given Operator `A` and Ket |`ψ`⟩.

# Examples

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
