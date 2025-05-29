```
compose(op::SymOperation, kv::KVec[, checkabc::Bool=true])  -->  KVec
```

Return the composition `op` $= \{\mathbf{W}|\mathbf{w}\}$ and a reciprocal-space vector `kv` $= \mathbf{k}$.

The operation is assumed to be specified the direct lattice basis, and `kv` in the reciprocal lattice basis. If both were specified in the Cartesian basis, `op` would act directly via its rotation part. However, because of the different bases, it now acts as:

$$
    \mathbf{k}' = (\mathbf{W}^{\text{T}})^{-1}\mathbf{k}.
$$

Note the transposition *and* inverse of $\mathbf{W}$, arising as a result of the implicit real-space basis of $\{\mathbf{W}|\mathbf{w}\}$ versus the reciprocal-space basis of $\mathbf{k}$ and the requirement that  $\mathbf{k} \cdot \mathbf{r} = \mathbf{k}' \cdot \mathbf{r}'$ for rotated (no translation, $\mathbf{w} = \mathbf{0}$) vectors$\mathbf{k}'$and$\mathbf{r}'``.

Note also that the composition of $\{\mathbf{W}|\mathbf{w}\}$ with $\mathbf{k}$ is independent of $\mathbf{w}$, i.e., translations do not act in reciprocal space.

## Extended help

If `checkabc = false`, the free part of `KVec` is not transformed (can be improve  performance in situations when `kabc` is zero, and several transformations are requested).
