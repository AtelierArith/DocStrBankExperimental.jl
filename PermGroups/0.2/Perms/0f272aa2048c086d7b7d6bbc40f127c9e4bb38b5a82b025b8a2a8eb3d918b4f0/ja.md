`invpermute(l::AbstractVector,p::Perm)`

は、`p` によって逆順に並べ替えられた `l` を返します。これは、`l` と同じ長さのベクトル `r` であり、`r[i^p]==l[i]` が `eachindex(l)` の `i` に対して成り立ちます。この関数は GAP 関数 `Permuted` に対応しますが、`invpermute(l,p)==invpermute!(copy(l),perm(p))` という Julia の慣習に合わせるために名前を変更しました。

```julia-repl
julia> invpermute([5,4,6],Perm(1,2,3))
3-element Vector{Int64}:
 6
 5
 4
```
