```
struct RotMatrixGenerator{N,T} <: RotationGenerator{N,T}
```

A statically-sized, N×N skew-symmetric matrix.

Note: the skew-symmetricity of the input matrix is *not* checked by the constructor.
