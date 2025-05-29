複合量子系の系 i に対する部分トレース

```jldoctest
julia> @op 𝒪 SpinBasis(1//2)⊗SpinBasis(1//2);

julia> op = ptrace(𝒪, 1)
tr1(𝒪)

julia> QuantumSymbolics.basis(op)
Spin(1/2)

julia> @op A; @op B;

julia> ptrace(A⊗B, 1)
(tr(A))B

julia> @ket k; @bra b;

julia> factorizable = A ⊗ (k*b)
A⊗|k⟩⟨b|

julia> ptrace(factorizable, 1)
(tr(A))|k⟩⟨b|

julia> ptrace(factorizable, 2)
(⟨b||k⟩)A

julia> mixed_state = (A⊗(k*b)) + ((k*b)⊗B)
(A⊗|k⟩⟨b|)+(|k⟩⟨b|⊗B)

julia> ptrace(mixed_state, 1)
(0 + ⟨b||k⟩)B+(tr(A))|k⟩⟨b|

julia> ptrace(mixed_state, 2)
(0 + ⟨b||k⟩)A+(tr(B))|k⟩⟨b|
```
