`leftdescents(W,w)`

コクセター群 `W` の要素 `w` の左降下、すなわち `length(W,W(i)*w)<length(W,w)` となる `i` の集合。

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> leftdescents(W,Perm(1,3))
2-element Vector{Int64}:
 1
 2
```
