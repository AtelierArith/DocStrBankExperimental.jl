`PermX(W::ComplexReflectionGroup,M::AbstractMatrix)`

`M`を`parent(W)`の根の集合を保持し、`W`を正規化する反射表現の可逆線形写像とします（右側の行列の作用に対して）。`PermX`は`parent(W)`の根の対応する置換を返します。`M`が`parent(W)`の根の集合を正規化しない場合は`nothing`を返します。

```julia-repl
julia> W=reflection_subgroup(rootdatum("E7sc"),1:6)
E₇₍₁₂₃₄₅₆₎=E₆Φ₁

julia> PermX(W,reflrep(W,longest(W)))==longest(W)
true
```
