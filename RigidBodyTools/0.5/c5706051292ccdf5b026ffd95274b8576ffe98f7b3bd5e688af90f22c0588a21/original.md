```
ForceTransform(xA_to_B::SVector,RA_to_B::SMatrix) -> ForceTransform
```

Computes the 6 x 6 Plucker transform matrix for force vectors, transforming from system A to system B. The input `xA_to_B` is the Euclidean vector from the origin of A to the origin of B, expressed in A coordinates, and `RA_to_B` is the rotation matrix transforming coordinates in system A to those in system B. The resulting matrix has the form

${}^B T^{(f)}_A = \begin{bmatrix} R & 0 \\ 0 & R \end{bmatrix} \begin{bmatrix} 1 & -x^\times \\ 0 & 1 \end{bmatrix}$
