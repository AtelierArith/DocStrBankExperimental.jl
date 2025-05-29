```
module KrylovDefaults
    const orth = KrylovKit.ModifiedGramSchmidtIR()
    const krylovdim = Ref(30)
    const maxiter = Ref(100)
    const tol = Ref(1e-12)
    const verbosity = Ref(KrylovKit.WARN_LEVEL)
end
```

A module listing the default values for the typical parameters in Krylov based algorithms:

  * `orth = ModifiedGramSchmidtIR()`: the orthogonalization routine used to orthogonalize the Krylov basis in the `Lanczos` or `Arnoldi` iteration
  * `krylovdim = 30`: the maximal dimension of the Krylov subspace that will be constructed
  * `maxiter = 100`: the maximal number of outer iterations, i.e. the maximum number of times the Krylov subspace may be rebuilt
  * `tol = 1e-12`: the tolerance to which the problem must be solved, based on a suitable error measure, e.g. the norm of some residual.

!!! warning
    The default value of `tol` is a `Float64` value, if you solve problems in `Float32` or `ComplexF32` arithmetic, you should always specify a new `tol` as the default value will not be attainable.

