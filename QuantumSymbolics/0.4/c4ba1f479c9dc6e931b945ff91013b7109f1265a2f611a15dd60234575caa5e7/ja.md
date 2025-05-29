量子オブジェクト（ケット、演算子、またはブラ）のテンソル積。

```jldoctest
julia> @ket k₁; @ket k₂;

julia> k₁ ⊗ k₂
|k₁⟩|k₂⟩

julia> @op A; @op B;

julia> A ⊗ B
A⊗B
```
