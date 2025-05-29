## Beam

Concrete structural element with transverse and moment loading.

### Constructor

```julia
Beam(ndim, nst, nxe, nip, direction, fin_el, axisymmetric)
```

### Arguments

```julia
* ndim::Int             : Number of dimensions
* nst::Int              : Number of stress terms
* nxe::Int              : Number of different property types
* nip::Int              : Number of integration points
* direction::Symbol     : Number of integration points
* fin_el::FiniteElement : Line(nod, nodof)
* axisymmetric::Bool    : Axisymmetric if true
```

### Related help

```julia
?StructuralElement      : Help on structural elements
?FiniteElement          : Help on finite element types
?Line                   : Help on a Line finite element
```
