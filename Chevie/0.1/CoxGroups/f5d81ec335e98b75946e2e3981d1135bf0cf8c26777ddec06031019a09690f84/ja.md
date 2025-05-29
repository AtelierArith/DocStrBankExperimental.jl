`isleftdescent(W::CoxeterGroup,w,i::Integer)`

は、Coxeter群 `W` の `i` 番目の生成反射が、要素 `w` の左降下集合に含まれている場合に `true` を返します。つまり、`length(W,W(i)*w)<length(W,w)` の場合です。

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> isleftdescent(W,Perm(1,2),1)
true
```
