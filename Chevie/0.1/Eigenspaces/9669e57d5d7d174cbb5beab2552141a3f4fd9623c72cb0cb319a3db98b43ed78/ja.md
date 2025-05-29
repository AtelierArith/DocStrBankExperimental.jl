`regular_eigenvalues(W)`

`W`を反射群または反射コセットとします。根の単位 `ζ` は、`W` のある要素が反射ハイパープレーンの外にある `ζ`-固有ベクトルを持つ場合、`W` の *正則固有値* です。この関数は、`W` の正則固有値のリストを返します。

```julia-repl
julia> regular_eigenvalues(coxgroup(:G,2))
6-element Vector{Root1}:
   1
  -1
  ζ₃
 ζ₃²
  ζ₆
 ζ₆⁵

julia> W=complex_reflection_group(6)
G₆

julia> L=twistings(W,[2])[4]
G₆₍₂₎=G₃‚₁‚₁[ζ₄]Φ′₄

julia> regular_eigenvalues(L)
3-element Vector{Root1}:
    ζ₄
  ζ₁₂⁷
 ζ₁₂¹¹
```
