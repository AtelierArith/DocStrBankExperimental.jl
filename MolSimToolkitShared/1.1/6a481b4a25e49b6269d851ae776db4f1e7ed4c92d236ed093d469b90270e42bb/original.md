```
align(x, y; mass = nothing)
align!(x, y; mass = nothing)
```

Aligns two structures (sets of points in 3D space). Solves the "Procrustes" problem, which is to find the best translation, and rotation, that aligns the two structures, minimizing the RMSD between them.

Structures are expected to be of the same size, and the  correspondence is assumed from the vector indices. 

`align` returns a new vector containing the coordinates of x aligned to y.  `align!` modifies the input vector `x` in place.
