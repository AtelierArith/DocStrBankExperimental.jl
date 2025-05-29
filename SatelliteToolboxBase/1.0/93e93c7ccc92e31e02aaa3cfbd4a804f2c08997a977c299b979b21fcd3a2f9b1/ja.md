```
Ellipsoid(a::T1, f::T2) where {T1 <: Number, T2 <: Number}
```

半長軸 `a` と扁平率 `f` を持つ楕円体を構築します（[`Ellipsoid`](@ref)を参照）。構造体内の他の要素は自動的に計算されます。

楕円体の型は、`T1` と `T2` を昇格させて `float` に変換することで得られます。
