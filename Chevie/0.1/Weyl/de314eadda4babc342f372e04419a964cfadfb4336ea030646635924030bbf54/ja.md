`describe_involution(W,w)`

コクセター群 `W` の反転 `w` に対して、[Richardson1982](biblio.htm#rich82) の定理により、`P` が `W` の唯一のパラボリック部分群であり、`P` が有限で、`w` が `P` の最長元であり、`P` の中心にあることが示されます。この関数は `P==reflection_subgroup(W,I)` かつ `w==longest(reflection_subgroup(W,I))` となる `I` を返します。

```julia-repl
julia> W=coxgroup(:A,2)
A₂

julia> w=longest(W)
(1,5)(2,4)(3,6)

julia> describe_involution(W,w)
1-element Vector{Int64}:
 3

julia> w==longest(reflection_subgroup(W,[3]))
true
```

現在のところ、有限コクセター群にのみ対応しています。
