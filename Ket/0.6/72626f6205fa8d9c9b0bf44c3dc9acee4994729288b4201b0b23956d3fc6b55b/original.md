```
random_unitary([T=ComplexF64,] d::Integer)
```

Produces a Haar-random unitary matrix in dimension `d`. If `T` is a real type the output is instead a Haar-random (real) orthogonal matrix.

References: Gilbert W. Stewart, [doi:10.1137/0717034](https://doi.org/10.1137/0717034)             Demmel et al., [lawn203](http://www.netlib.org/lapack/lawnspdf/lawn203.pdf)
