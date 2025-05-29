```
A, E = qnm_pep_companion(TFC, pep::AbstractVector{<:AbstractMatrix}) where TFC <: Union{AbstractFloat, Complex{<:AbstractFloat}}
```

Linearizes a polynomial eigenvalue problem (PEP) and returns the companion form, as in the paper by Mehrmann and Voss. More precisely, for a k-th degree PEP with n-by-n coefficient matrices, this returns matrices A and E, both kn-by-kn, corresponding to the linearized problem

$$
Ax = λEx
$$

# References

  * [mehrmann2004nonlinear](@citet*)
  * [NonlinearEigenproblems.jl/src/method_companion.jl at master · nep-pack/NonlinearEigenproblems.jl](https://github.com/nep-pack/NonlinearEigenproblems.jl/blob/master/src/method_companion.jl)
