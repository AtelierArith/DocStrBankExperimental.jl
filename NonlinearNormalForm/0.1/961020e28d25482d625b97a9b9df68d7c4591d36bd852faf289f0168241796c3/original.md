```
checksymp(M)
```

Returns `tranpose(M)*S*M - S`, where `S` is the skew-symmetric matrix  `S = blkdiag([0 1; -1 0], ...)`. If `M` is symplectic, then the result should be a matrix  containing all zeros. The non-symplectic parts of the matrix can be identified  by those nonzero elements in the result.
