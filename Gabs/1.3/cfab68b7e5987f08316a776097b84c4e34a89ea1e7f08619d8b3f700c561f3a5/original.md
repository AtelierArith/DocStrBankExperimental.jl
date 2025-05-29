```
blochmessiah(state::GaussianUnitary) -> BlochMessiah
```

Compute the Bloch-Messiah/Euler decomposition of the `symplectic` field of a `GaussianUnitary` and return a `BlockMessiah` object.

The orthogonal symplectic matrices `O` and `Q` as well as the singular values `values` can be obtained via `F.O`, `F.Q`, and `F.values`, respectively.

Iterating the decomposition produces the components `O`, `values`, and `Q`, in that order.
