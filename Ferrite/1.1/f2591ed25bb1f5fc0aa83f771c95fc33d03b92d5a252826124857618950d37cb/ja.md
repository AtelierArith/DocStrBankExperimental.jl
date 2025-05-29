```
collect_periodic_facets(grid::Grid, mset, iset, transform::Union{Function,Nothing}=nothing; tol=1e-12)
```

`mset`内のすべてのミラーフェイシットを、`iset`内の対応するイメージフェイシットと一致させます。各ミラーフェイシットをイメージフェイシットにマッピングする辞書を返します。この結果は、[`PeriodicDirichlet`](@ref)に渡すことができます。

`mset`と`iset`は、グリッド内の既存のフェイシットセットとして`String`で指定するか、直接`AbstractSet{FacetIndex}`として指定できます。

デフォルトでは、この関数は座標系の方向に一致するフェイシットを探します。他のタイプの周期性には、`transform`関数を使用できます。`transform`関数はイメージフェイシットの座標に適用され、一致するミラーセット内の位置に座標を変換することが期待されます。

キーワード`tol`は、イメージフェイシットとミラーフェイシットの間で一致と見なされるための許容範囲（すなわち、距離とフェイシット法線の偏差）を指定します。

関連情報: [`collect_periodic_facets!`](@ref), [`PeriodicDirichlet`](@ref).
