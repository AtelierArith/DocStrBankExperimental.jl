`diagconj_elt(M,N)`

`M` and `N` must be square matrices of the same size. This function returns a vector `d` such that `N==inv(Diagonal(d))*M*Diagonal(d)` if such a vector exists, and `nothing` otherwise.

```julia_repl
julia> M=[1 2;2 1];N=[1 4;1 1]
2×2 Matrix{Int64}:
 1  4
 1  1

julia> diagconj_elt(M,N)
2-element Vector{Rational{Int64}}:
 1
 2
```
