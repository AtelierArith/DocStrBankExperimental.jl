## FiniteElement

抽象有限要素型。

### 型

```julia
abstract type FiniteElement end
```

### サブタイプ

```julia
* Line::FiniteElement          : 1D Line(nod, nodof)
* Triangle::FiniteElement      : 2D Triangle(nod, nodof)
* Quadrilateral::FiniteElement : 2D Quadrilateral(nod, nodof)
* Hexahedron::FiniteElement    : 3D Hexahedron(nod, nodof)
* Tetrahedron::FiniteElement   : 3D Tetrahedron(nod, nodof)
```
