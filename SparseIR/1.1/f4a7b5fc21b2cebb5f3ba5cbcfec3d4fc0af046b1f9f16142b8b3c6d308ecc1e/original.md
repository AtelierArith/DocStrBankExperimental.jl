```
DiscreteLehmannRepresentation <: AbstractBasis
```

Discrete Lehmann representation (DLR) with poles selected according to extrema of IR.

This class implements a variant of the discrete Lehmann representation (`DLR`) [1](https://doi.org/10.48550/arXiv.2110.06765). Instead of a truncated singular value expansion of the analytic continuation kernel $K$ like the IR, the discrete Lehmann representation is based on a "sketching" of $K$. The resulting basis is a linear combination of discrete set of poles on the real-frequency axis, continued to the imaginary-frequency axis:

```
 G(iv) == sum(a[i] / (iv - w[i]) for i in range(L))
```

Warning The poles on the real-frequency axis selected for the DLR are based on a rank-revealing decomposition, which offers accuracy guarantees. Here, we instead select the pole locations based on the zeros of the IR basis functions on the real axis, which is a heuristic. We do not expect that difference to matter, but please don't blame the DLR authors if we were wrong :-)
