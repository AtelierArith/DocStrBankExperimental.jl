```
KrylovSubspace{T}(n,[maxiter=30]) -> Ks
KrylovSubspace{T, U, VType}(n,[maxiter=30]) -> Ks
```

Constructs an uninitialized Krylov subspace, which can be filled by `arnoldi!`.

The dimension of the subspace, `Ks.m`, can be dynamically altered but should be smaller than `maxiter`, the maximum allowed arnoldi iterations.

The type of the (extended) orthonormal basis vector matrix `V` may be specified as `VType`. This is required e. g. for `GPUArray`s. 

`U` determines `eltype(H)`.

```
getV(Ks) -> V
getH(Ks) -> H
```

Access methods for the (extended) orthonormal basis `V` and the (extended) Gram-Schmidt coefficients `H`. Both methods return a view into the storage arrays and has the correct dimensions as indicated by `Ks.m`.

```
resize!(Ks, maxiter) -> Ks
```

Resize `Ks` to a different `maxiter`, destroying its contents.

This is an expensive operation and should be used scarcely.
