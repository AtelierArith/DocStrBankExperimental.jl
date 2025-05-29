```julia
factorize(ABA)

```

Evaluates the LU factorization matrices of the ABA matrix, using KLU.

# Arguments

  * `ABA::ABA_Matrix{Ax, L, Nothing} where {Ax, L <: NTuple{2, Dict}}`:       container for the ABA matrix, with ABA.K == nothing (LU matrices in K not evaluated)
