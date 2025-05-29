## Rod

Concrete 1D structural element with only axial stresses.

### Constructor

```julia
Rod(nels, np_types, nip, fin_el)
```

### Arguments

```julia
* nels::Int             : Number of fin_els (stored in field nxe)
* np_types::Int         : Number of different property types
* nip::Int              : Number of integration points
* fin_el::FiniteElement : Line(nod, nodof)
```

### Related help

```julia
?StructuralElement      : Help on structural elements
?FiniteElement          : Help on finite element types
?Line                   : Help on a Line finite element
```
