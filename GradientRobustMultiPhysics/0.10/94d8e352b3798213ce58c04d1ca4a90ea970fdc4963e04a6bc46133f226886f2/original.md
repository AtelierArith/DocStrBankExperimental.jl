```
function FESpace{FEType<:AbstractFiniteElement,AT<:AssemblyType}(
    xgrid::ExtendableGrid{Tv,Ti};
    name = "",
    broken::Bool = false)
```

Constructor for FESpace of the given FEType, AT = ON*CELLS/ON*FACES/ON*EDGES generates a finite elements space on the cells/faces/edges of the provided xgrid (if omitted ON*CELLS is used as default). The broken switch allows to generate a broken finite element space (that is piecewise H1/Hdiv/HCurl). If no name is provided it is generated automatically from FEType. If no AT is provided, the space is generated ON_CELLS.
