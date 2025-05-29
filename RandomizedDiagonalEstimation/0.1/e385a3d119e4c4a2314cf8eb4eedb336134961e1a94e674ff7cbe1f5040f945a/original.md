```
function EstimateFunctionDiagonal(A::Matrix{Float64},fmat,f,Algorithm::Symbol, StoppingCriterion::Symbol, distribution::Symbol, MatFuncApprox::Symbol, deg::Int64, normalizationParam::Bool=true;maxqueries::Int,int::Tuple=(0.0,1.0),q=4,O=nothing)
```

Main function to compute a randomized estimate of the diagonal of a matrix function

Input:

  * A: Matrix as input for the function
  * f: Function to approximate diagonal of
  * Algorithm: Choose which diagonal estimator is used, options are

      * :GirardHutchinson
      * :funDiagPP
      * :funNys
  * MatFuncApprox: How to approximate f(A)b

      * Chebshev: Using Chebyshev polynomials

          * requires interval int and degree deg
      * Remez: Using Remez polynomials

          * requires interval int and degree deg
      * Krylov: Using the Arnoldi approximation

          * requires maximum potency of A in the Krylov subspace denoted by deg
      * CG: Use conjugate gradient method to approximate diagonal of the inverse, Attention: f is neglected

          * requires maximum potency of A in the Krylov subspace denoted by deg
  * StoppingCriterion: How to terminate, possible options

      * queries: terminate when the maximum number of queries to A is reacher

          * maxqueries: maximum number of queries to A
  * distribution: Select the distribution from which the random vectors are drawn, inbuilt options are

      * :Rademacher
      * :Gaussion
      * :custom, in this case provide a matrix with the test vectors as columns

          * O: matrix with the test vectors as columns
  * deg: degree of polynomial or maximum potency of A in the Krylov subspace, depending on MatFuncApprox
