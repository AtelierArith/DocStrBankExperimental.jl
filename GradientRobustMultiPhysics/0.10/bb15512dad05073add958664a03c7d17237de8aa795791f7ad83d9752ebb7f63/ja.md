```
abstract type H1BUBBLE{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

境界でゼロとなる区分的バブル

許可される要素の幾何学:

  * Edge1D (1つの二次バブル)
  * Triangle2D (1つの三次バブル)
  * Quadrilateral2D (1つの四次バブル)
  * Tetrahedron3D (1つの三次バブル)
