```
cross_vector(M::SMatrix) -> SVector
```

Takes a matrix `M` and forms the corresponding axial vector `v` from the matrix's anti-symmetric part ($M_a = (M-M^{T})/2$), so that $v \times w$ is equivalent to $M_a\cdot w$.
