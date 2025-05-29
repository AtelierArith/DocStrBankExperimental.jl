Tensor product of quantum objects (kets, operators, or bras).

```jldoctest
julia> @ket k₁; @ket k₂;

julia> k₁ ⊗ k₂
|k₁⟩|k₂⟩

julia> @op A; @op B;

julia> A ⊗ B
A⊗B
```
