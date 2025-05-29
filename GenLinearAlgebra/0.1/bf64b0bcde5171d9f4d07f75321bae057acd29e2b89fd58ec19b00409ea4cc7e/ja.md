`diagconj_elt(M,N)`

`M` と `N` は同じサイズの正方行列でなければなりません。この関数は、`N==inv(Diagonal(d))*M*Diagonal(d)` となるベクトル `d` を返します。もしそのようなベクトルが存在しない場合は `nothing` を返します。

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
