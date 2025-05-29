```
qexpand(s)
```

Manually expand a symbolic expression of quantum objects. 

```jldoctest
julia> @op A; @op B; @op C;

julia> qexpand(commutator(A, B))
-1BA+AB

julia> qexpand(A⊗(B+C))
(A⊗B)+(A⊗C)

julia> @ket k₁; @ket k₂;

julia> qexpand(A*(k₁+k₂))
A|k₁⟩+A|k₂⟩
```
