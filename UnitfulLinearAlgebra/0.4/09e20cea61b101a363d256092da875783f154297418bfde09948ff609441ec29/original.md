```
svd(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD

Singular value decomposition (SVD) of `AbstractMultipliableMatrix`.
Only exists for uniform matrices (pp. 124, Hart, 1995).
Functions for `SVD{AbstractMultipliableMatrix}` object: `inv`, `size`, `adjoint`, `svdvals`.
Not implemented: `ldiv!`.
```
