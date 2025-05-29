## GenericSolid

Solid structural element.

### Constructor

```julia
GenericSolid(ndim, nst, nels, nn, nip, finite_element(nod, nodof), axisymmetric)
```

### Arguments

```julia
* ndim::Int               : Number of dimensions
* nst::Int                : Number of stress terms
* nels::Int               : Number of finite elements
* nn::Int                 : Number of nodes
* nip::Int                : Number of integration points
* fin_el::FiniteElement   : Finite element type used
* axisymmetric::Bool      : Axisymmetric
```

### Related help

```julia
?StructuralElement  : List structural elements
?FiniteElement      : List finite element types
```
