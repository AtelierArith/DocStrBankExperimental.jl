Symbolic anticommutator of two operators.

```jldoctest
julia> @op A; @op B;

julia> anticommutator(A, B)
{A,B}
```
