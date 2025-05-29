## Solid

Solid structural element.

### Constructor

```julia
Solid(ndim, nst, nxe, nye, nze, nip, finite_element(nod, nodof))
```

### Arguments

```julia
* ndim::Int             : Number of dimensions
* nst::Int              : Number of stress terms
* nxe::Int              : Number of elements in x direction
* nye::Int              : Number of elements in y direction
* nze::Int              : Number of elements in z direction
* nip::Int              : Number of integration points
* fin_el::FiniteElement : Line(nod, nodof)
```

### Related help

```julia
?StructuralElement  : List structural elements
?FiniteElement      : List finite element types
```
