`PermY(W::ComplexReflectionGroup,M::AbstractMatrix)`

`M` を `W` の反射表現の双対上の可逆線形写像とし、`parent(W)` のコルートの集合を保持し、`W` を正規化する（右側の行列の作用に対して）とします。`PermY` は `parent(W)` のコルートの対応する置換を返します；もし `M` が `parent(W)` のコルートの集合を正規化しない場合は `nothing` を返します。

```julia-repl
julia> W=reflection_subgroup(rootdatum("E7sc"),1:6)
E₇₍₁₂₃₄₅₆₎=E₆Φ₁

julia> PermY(W,YMatrix(W,longest(W)))==longest(W)
true
```
