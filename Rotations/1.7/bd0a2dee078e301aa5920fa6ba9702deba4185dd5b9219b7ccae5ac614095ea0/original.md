```
struct RotMatrix{N,T} <: Rotation{N,T}
```

A statically-sized, N×N unitary (orthogonal) matrix.

Note: the orthonormality of the input matrix is *not* checked by the constructor.
