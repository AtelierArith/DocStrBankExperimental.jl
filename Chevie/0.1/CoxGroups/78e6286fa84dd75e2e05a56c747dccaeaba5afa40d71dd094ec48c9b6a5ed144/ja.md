`elements(W::CoxeterGroup[,l])`

`l` が指定されていない場合、これは `W` が有限である場合にのみ機能します; それはコクセター長が増加する順に `W` の要素を返します。第二引数が整数 `l` の場合、コクセター長 `l` の `W` の要素が返されます。

```julia_repl
julia> W=coxgroup(:G,2)
G₂

julia> e=elements(W,6)
1-element Vector{Perm{Int16}}:
 (1,7)(2,8)(3,9)(4,10)(5,11)(6,12)

julia> e[1]==longest(W)
true
```
