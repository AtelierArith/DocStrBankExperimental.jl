```
transformation(h1::Hook, h2::Hook)
```

`h1`に`h2`を合わせるための`CoordinateTransformation`を返します。

フック`h1, h2`がそれぞれ`CoordinateSystem`s `h1cs, h2cs`に対して相対的な場合、`push!(h1cs.refs, sref(h2cs, origin, rot=rotation, xrefl=xrefl))`を使用して`h1cs`内で`h2cs`を参照すると、`h1cs`に対して相対的に`h2`は`h1`の上に位置し、その`in_direction`は`h1`のそれと反対を向き（適用可能な場合は手の向きも一致します）。
