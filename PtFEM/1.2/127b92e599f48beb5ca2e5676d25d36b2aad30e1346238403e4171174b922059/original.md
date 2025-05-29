## StructuralElement

Abstract structural element type.

### Type

```julia
abstract type StructuralElement end
```

### Subtypes

```julia
* Rod::StructuralElement          : Rod(nxe, np_types, nip, fin_el)
* Beam::StructuralElement         : Beam(nod, nodof)
* Frame::StructuralElement        : Frame(nod, nodof)
* Plane::StructuralElement        : Plane(nod, nodof)
* Solid::StructuralElement        : Solid(nod, nodof)
* GenericSolid::StructuralElement : GenericSolid(nod, nodof)
```

### Related help

```julia
?FiniteElement                    : Show all finite elements
?Rod                              : Help on Rod structural element
?Beam                             : Help on Beam structural element
?Frame                            : Help on Frame structural element
?Plane                            : Help on Plane structural element
?Solid                            : Help on Solid structural element
?GenericSolid                     : Help on GenericSolid structural element
```
