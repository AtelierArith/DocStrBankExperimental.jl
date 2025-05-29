`isrightdescent(W::CoxeterGroup,w,i::Integer)`

は、コクセター群 `W` の `i` 番目の生成反射が、要素 `w` の右降下集合に含まれている場合に `true` を返します。つまり、`length(W,w*W(i))<length(W,w)` の場合です。

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> isrightdescent(W,Perm(1,2),1)
true
```
