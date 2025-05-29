`bruhatless(W, y)`

は、`W` の中で Bruhat 順序において `w` より小さく、コクセター長が `i-1` の要素のベクトルを持つベクトルを返します。したがって、返されるリストの最初の要素には `one(W)` のみが含まれ、`length(W,w)`-th 要素には `w` のみが含まれます。

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> bruhatless(W,Perm(1,3))
4-element Vector{Vector{Perm{Int16}}}:
 [()]
 [(1,2), (2,3)]
 [(1,2,3), (1,3,2)]
 [(1,3)]
```

Coxeter 群については [`bruhatPoset`](@ref) も参照してください。
