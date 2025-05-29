`invariant_form(W::ComplexReflectionGroup)`

この関数は、反射群 `W` の作用に対して不変なエルミート形式の行列 `F`（スカラーに対して定義される）を返します。つまり、`M` が `W` の要素の行列である場合、`M*F*M'=F` となります。

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> invariant_form(W)
2×2 Matrix{Int64}:
 1  0
 0  2
```
