Transpose of quantum objects (kets, bras, operators).

```jldoctest
julia> @op A; @op B; @ket k;

julia> transpose(A)
Aᵀ

julia> transpose(A+B)
Aᵀ+Bᵀ

julia> transpose(k)
|k⟩ᵀ
```
