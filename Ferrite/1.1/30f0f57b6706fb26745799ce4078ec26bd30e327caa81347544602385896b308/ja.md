```
Interpolation{ref_shape, order}()
```

`ref_shape`（[`AbstractRefShape`](@ref）を参照）上で定義された補間のための抽象型です。`order`は補間の次数に対応します。補間は、ノード間で関数を補間するための形状関数を定義するために使用されます。

以下の補間が実装されています：

  * `Lagrange{RefLine, 1}`
  * `Lagrange{RefLine, 2}`
  * `Lagrange{RefQuadrilateral, 1}`
  * `Lagrange{RefQuadrilateral, 2}`
  * `Lagrange{RefQuadrilateral, 3}`
  * `Lagrange{RefTriangle, 1}`
  * `Lagrange{RefTriangle, 2}`
  * `Lagrange{RefTriangle, 3}`
  * `Lagrange{RefTriangle, 4}`
  * `Lagrange{RefTriangle, 5}`
  * `BubbleEnrichedLagrange{RefTriangle, 1}`
  * `CrouzeixRaviart{RefTriangle, 1}`
  * `CrouzeixRaviart{RefTetrahedron, 1}`
  * `RannacherTurek{RefQuadrilateral, 1}`
  * `RannacherTurek{RefHexahedron, 1}`
  * `Lagrange{RefHexahedron, 1}`
  * `Lagrange{RefHexahedron, 2}`
  * `Lagrange{RefTetrahedron, 1}`
  * `Lagrange{RefTetrahedron, 2}`
  * `Lagrange{RefPrism, 1}`
  * `Lagrange{RefPrism, 2}`
  * `Lagrange{RefPyramid, 1}`
  * `Lagrange{RefPyramid, 2}`
  * `Serendipity{RefQuadrilateral, 2}`
  * `Serendipity{RefHexahedron, 2}`
  * `Nedelec{RefTriangle, 1}`
  * `Nedelec{RefTriangle, 2}`
  * `Nedelec{RefQuadrilateral, 1}`
  * `Nedelec{RefTetrahedron, 1}`
  * `Nedelec{RefHexahedron, 1}`
  * `RaviartThomas{RefTriangle, 1}`
  * `RaviartThomas{RefTriangle, 2}`
  * `RaviartThomas{RefQuadrilateral, 1}`
  * `RaviartThomas{RefTetrahedron, 1}`
  * `RaviartThomas{RefHexahedron, 1}`
  * `BrezziDouglasMarini{RefTriangle, 1}`

さらに、`DiscontinuousLagrange`は、`Lagrange`と同じ参照形状および次数に対して実装されており、任意の参照形状に対して`order = 0`でも実装されています。

# 例

```jldoctest
julia> ip = Lagrange{RefTriangle, 2}()
Lagrange{RefTriangle, 2}()

julia> getnbasefunctions(ip)
6
```
