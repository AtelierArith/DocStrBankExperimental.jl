## FiniteElement

Abstract finite element type.

### Type

```julia
abstract type FiniteElement end
```

### Subtypes

```julia
* Line::FiniteElement          : 1D Line(nod, nodof)
* Triangle::FiniteElement      : 2D Triangle(nod, nodof)
* Quadrilateral::FiniteElement : 2D Quadrilateral(nod, nodof)
* Hexahedron::FiniteElement    : 3D Hexahedron(nod, nodof)
* Tetrahedron::FiniteElement   : 3D Tetrahedron(nod, nodof)
```
