```
PluckerForce(data::AbstractVector)
```

Creates an instance of a Plucker force vector,

$f = \begin{bmatrix} M \\ F \end{bmatrix}$

using the vector in `data`. If `data` is of length 6, then it creates a 3d force vector, and the first 3 entries are assumed to comprise the moment component `M` and the last 3 entries the force component `F`. If `data` is of length 3, then it creates a 2d force vector, assuming that the first entry in `data` represents the moment component and the second and third entries the x and y force components.
