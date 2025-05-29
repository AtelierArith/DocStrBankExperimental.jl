量子オブジェクトの転置（ケット、ブラ、演算子）。

```jldoctest
julia> @op A; @op B; @ket k;

julia> transpose(A)
Aᵀ

julia> transpose(A+B)
Aᵀ+Bᵀ

julia> transpose(k)
|k⟩ᵀ
```
