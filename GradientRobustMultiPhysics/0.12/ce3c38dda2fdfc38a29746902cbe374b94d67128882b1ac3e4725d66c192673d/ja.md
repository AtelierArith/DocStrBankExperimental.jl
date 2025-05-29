```
abstract type H1P1TEB{edim} <: AbstractH1FiniteElementWithCoefficients where {edim<:Int}
```

ベクトル値（ncomponents = edim）の要素で、P1関数と、["Fortin Operator for the Taylor-Hood Element", 2021, arxiv:2104.13953]で提案された接線加重エッジバブルを使用します。

（連続P1圧力空間と組み合わせるとStokesに対してinf-sup安定であり、MINIよりも自由度が少ない）

許可されるElementGeometries:

  * Triangle2D
  * Tetrahedron3D
