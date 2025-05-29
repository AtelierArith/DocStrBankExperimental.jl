`cycletype(p::SPerm,n=last_moved(p))` は、ハイパーオクタhedral群 `Bₙ` における `p` の共役類をパラメータ化する分割のペアです。

```julia-repl
julia> cycletype(SPerm(1,-1),2)
2-element Vector{Vector{Int64}}:
 [1]
 [1]
```
