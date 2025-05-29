```
PluckerMotion(data::AbstractVector)
```

Creates an instance of a Plucker motion vector,

$v = \begin{bmatrix} \Omega \\ U \end{bmatrix}$

using the vector in `data`. If `data` is of length 6, then it creates a 3d motion vector, and the first 3 entries are assumed to comprise the rotational component `\Omega` and the last 3 entries the translational component `U`. If `data` is of length 3, then it creates a 2d motion vector, assuming that the first entry in `data` represents the rotational component and the second and third entries the x and y translational components.
