```julia
mutable struct BoundaryData{BDT<:GradientRobustMultiPhysics.AbstractBoundaryType, MType, FType}
```

collects boundary data for a component of the system and allows to specify a AbstractBoundaryType for each boundary region so far only DirichletBoundary types (see above)
