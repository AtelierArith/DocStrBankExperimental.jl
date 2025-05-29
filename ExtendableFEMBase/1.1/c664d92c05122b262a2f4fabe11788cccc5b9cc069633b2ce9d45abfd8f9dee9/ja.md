```
抽象型 H1P1TEB{edim} <: AbstractH1FiniteElementWithCoefficients where {edim<:Int}
```

ベクトル値（ncomponents = edim）の要素で、P1関数と、[Diening, L., Storn, J. & Tscherpel, T., "Fortin operator for the Taylor–Hood element", Num. Math. 150, 671–689 (2022)] によって提案された接線重み付きエッジバブルを使用します。

（連続P1圧力空間と組み合わせるとStokesに対してinf-sup安定であり、MINIよりも自由度が少ない）

許可されるElementGeometries:

  * Triangle2D
  * Tetrahedron3D
