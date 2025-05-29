## Plane

Plate structural element.

### Constructor

```julia
Plane(ndim, nst, nxe, nye, nip, dir, finite_element(nod, nodof), axisymmetric)
```

### Arguments

```julia
* ndim::Int               : Number of dimensions
* nst::Int                : Number of stress terms
* nxe::Int                : Number of elements in x direction
* nye::Int                : Number of elements in y direction
* nip::Int                : Number of integration points
* dir::Symbol             : Direction of node numbering
* fin_el::FiniteElement   : Line(nod, nodof)
* axisymmetric::Bool      : Axisymmetric
```

### Related help

```julia
?StructuralElement  : List structural elements
?FiniteElement      : List finite element types
?Line               : Help on a Line finite element
```
