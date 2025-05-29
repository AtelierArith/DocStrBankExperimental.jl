Trace of an operator

```jldoctest
julia> @op A; @op B;

julia> tr(A)
tr(A)

julia> tr(commutator(A, B))
0

julia> @bra b; @ket k;

julia> tr(k*b)
⟨b||k⟩
```
