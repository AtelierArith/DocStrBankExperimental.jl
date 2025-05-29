```
TruncVUMPS{TI, TF} <: SVDTrunc
```

A type used to perform  truncations of an [`InfiniteUniformTensorTrain`](@ref) to a target bond size `d`. It uses the Variational Uniform Matrix Product States (VUMPS) algorithm from MPSKit.jl.

# FIELDS

  * `d`: target bond dimension
  * `maxiter = 100`: max number of iterations for the VUMPS algorithm
  * `tol = 1e-14`: tolerance for the VUMPS algorithm

```@example
p = rand_infinite_uniform_tt(10, 2, 2)
compress!(p, TruncVUMPS(5))
```
