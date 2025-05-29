`graph_automorphisms(t::Vector{TypeIrred})`

有限コクセター群の `refltype` を与えると、`indices(t)` の置換の群としての `t` のすべてのグラフ自己同型の群を返します。

```julia-repl
julia> W=coxgroup(:D,4)
D₄

julia> graph_automorphisms(refltype(W*W))
Group((1,5)(2,6)(3,7)(4,8),(1,2),(1,4))
```
