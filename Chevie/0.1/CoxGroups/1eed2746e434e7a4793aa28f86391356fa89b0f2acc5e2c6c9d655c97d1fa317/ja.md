`words(W::CoxeterGroup[,l::Integer])`

1つの引数で、これは`W`が有限の場合にのみ機能します。`W`の要素の縮約されたコクセター単語を長さが増加する順に返します。2番目の引数が整数`l`の場合、長さ`l`の要素のみが返されます。これは無限コクセター群でも機能します。

```julia_repl
julia> W=coxgroup(:G,2)
G₂

julia> e=elements(W,6)
1-element Vector{Perm{Int16}}:
 (1,7)(2,8)(3,9)(4,10)(5,11)(6,12)

julia> e[1]==longest(W)
true
```
