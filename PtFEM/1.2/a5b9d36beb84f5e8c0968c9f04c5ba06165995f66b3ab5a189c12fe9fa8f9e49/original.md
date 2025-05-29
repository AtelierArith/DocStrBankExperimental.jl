## Frame

Pin- or rigid-jointed structural element.

### Constructor

```julia
Frame(nels, nn, ndim, finite_element(nod, nodof))
```

### Arguments

```julia
* nels::Int             : Number of elements
* nn:Int                : Number of nodes
* ndim::Int             : Number of dimensions
* nst::Int              : Number of stress terms
* nip::Int              : Number of integration points
* fin_el::FiniteElement : Line(nod, nodof)
```

### Related help

```julia
?StructuralElement  : List structural elements
?FiniteElement      : List finite element types
?Line               : Help on a Line finite element
```
