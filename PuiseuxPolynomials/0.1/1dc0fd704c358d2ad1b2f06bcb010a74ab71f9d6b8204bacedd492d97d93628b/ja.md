`scalar(p::Mvp)`

もし `p` がスカラーであれば、そのスカラーを返し、そうでなければ `nothing` を返します。

```julia-repl
julia> p=Mvp(:x)+1
Mvp{Int64}: x+1

julia> w=p(x=4)
Mvp{Int64}: 5

julia> scalar(w)
5

julia> typeof(scalar(w))
Int64
```

もし `p` が配列であれば、その要素に `scalar` を適用し、スカラーでない `Mvp` が含まれている場合は `nothing` を返します。
