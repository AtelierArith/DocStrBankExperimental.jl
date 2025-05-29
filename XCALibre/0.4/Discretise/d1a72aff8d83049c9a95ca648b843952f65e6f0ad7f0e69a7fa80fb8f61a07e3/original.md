```
DirichletFunction(ID, value) <: AbstractDirichlet
```

Dirichlet boundary condition defined with user-provided function.

# Input

  * `ID` Boundary name provided as symbol e.g. :inlet
  * `value` Custom function for Dirichlet boundary condition.

# Function requirements

The function passed to this boundary condition must have the following signature:

```
f(coords, time, index) = SVector{3}(ux, uy, uz)
```

Where, `coords` is a vector containing the coordinates of a face, `time` is the current time in transient simulations (and the iteration number in steady simulations), and `index` is the local face index (from 1 to `N`, where `N` is the number of faces in a given boundary). The function must return an SVector (from StaticArrays.jl) representing the velocity vector. 
