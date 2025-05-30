二つの演算子の象徴的な交換子。

```jldoctest
julia> @op A; @op B;

julia> commutator(A, B)
[A,B]

julia> commutator(A, A)
𝟎
```
