```
MotionTransform(xA_to_B::SVector,RA_to_B::SMatrix) -> MotionTransform
```

Computes the Plucker transform matrix for motion vectors, transforming from system A to system B. The input `xA_to_B` is the Euclidean vector from the origin of A to the origin of B, expressed in A coordinates, and `RA_to_B` is the rotation matrix transforming coordinates in system A to those in system B. The resulting matrix has the form

${}^B T^{(m)}_A = \begin{bmatrix} R & 0 \\ 0 & R \end{bmatrix} \begin{bmatrix} 1 & 0 \\ -x^\times & 1 \end{bmatrix}$

One can also provide `xA_to_B` as a standard vector and `RA_to_B` as a standard 3 x 3 matrix.

If `xA_to_B` has length 3, then a three-dimensional transform (a 6 x 6 Plucker transform) is created. If `xA_to_B` has length 2, then a two-dimensional transform (3 x 3 Plucker transform) is returned.
