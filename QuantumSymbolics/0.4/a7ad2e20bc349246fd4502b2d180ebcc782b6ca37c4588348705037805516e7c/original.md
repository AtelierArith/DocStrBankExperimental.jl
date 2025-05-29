Symbolic commutator of two operators.

```jldoctest
julia> @op A; @op B;

julia> commutator(A, B)
[A,B]

julia> commutator(A, A)
𝟎
```
