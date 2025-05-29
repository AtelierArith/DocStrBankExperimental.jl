二つの演算子の象徴的な反交換子。

```jldoctest
julia> @op A; @op B;

julia> anticommutator(A, B)
{A,B}
```
