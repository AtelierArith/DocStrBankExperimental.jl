`firstleftdescent(W,w)`

は、`w` の左降下集合の最初の要素の `gens(W)` におけるインデックスを返します。つまり、最初の `i` であって、もし `s=W(i)` ならば `l(sw)<l(w)` となるものです。`one(W)` に対しては `nothing` を返します。

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> firstleftdescent(W,Perm(2,3))
2
```
