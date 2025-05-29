```
Interpolation{ref_shape, order}()
```

Abstract type for interpolations defined on `ref_shape` (see [`AbstractRefShape`](@ref)). `order` corresponds to the order of the interpolation. The interpolation is used to define shape functions to interpolate a function between nodes.

The following interpolations are implemented:

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

Additionally, `DiscontinuousLagrange` is implemented for the same reference shapes and orders as `Lagrange`, as well as for `order = 0` on any reference shape.

# Examples

```jldoctest
julia> ip = Lagrange{RefTriangle, 2}()
Lagrange{RefTriangle, 2}()

julia> getnbasefunctions(ip)
6
```
