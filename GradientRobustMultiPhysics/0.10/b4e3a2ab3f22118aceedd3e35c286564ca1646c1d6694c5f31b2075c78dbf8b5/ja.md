```
abstract type H1BR{edim} <: AbstractH1FiniteElementWithCoefficients where {edim<:Int}
```

ベクトル値（ncomponents = edim）Bernardi–Raugel要素（一次多項式 + 正規加重面バブル）

許可されるElementGeometries:

  * Triangle2D（区分線形 + 正規加重面バブル）
  * Quadrilateral2D（Q1空間 + 正規加重面バブル）
  * Tetrahedron3D（区分線形 + 正規加重面バブル）
