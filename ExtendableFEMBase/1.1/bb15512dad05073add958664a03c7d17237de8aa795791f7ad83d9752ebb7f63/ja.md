```
抽象型 H1BUBBLE{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

境界でゼロの区分的バブル

許可される要素幾何学:

  * Edge1D (1つの二次バブル)
  * Triangle2D (1つの三次バブル)
  * Quadrilateral2D (1つの四次バブル)
  * Tetrahedron3D (1つの三次バブル)
