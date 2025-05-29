`semisimpleRank(W::ComplexReflectionGroup)`

は `W` の *半単純階数* を返します。これは、`W` が実際に作用する空間の次元です。もし `W` が空間 `V` 上の反射群であり、`V₁` が `roots(W)` によって生成される部分空間であるならば、`semisimplerank(W)` は `V₁` の次元です。反射群 `W` は、`V₁=V` の場合に *本質的* と呼ばれます。

```julia-repl
julia> W=reflection_subgroup(coxgroup(:A,3),[1,3])
A₃₍₁₃₎=A₁×A₁Φ₁

julia> semisimplerank(W)
2

julia> rank(W)
3
```
