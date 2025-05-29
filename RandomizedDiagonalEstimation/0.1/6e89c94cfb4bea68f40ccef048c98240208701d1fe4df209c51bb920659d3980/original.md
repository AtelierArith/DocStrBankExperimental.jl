```
function EstimateDiagonal(A::Matrix{Float64},Algorithm::Symbol, StoppingCriterion::Symbol, distribution::Symbol, normalizationParam::Bool=true, parallelizationParam::Bool=false ;maxqueries::Int=0,O=nothing,var_est::Float64=1/eps(),epsilon::Float64=1.0, delta::Float64=1.0,con::Float64=1.0)
```

Main function to compute a randomized estimate of the diagonal of a matrix A

Input:

  * A: Matrix to estimate the diagonal of
  * Algorithm: Choose which diagonal estimator is used, options are

      * :GirardHutchinson
      * DiagPP
      * :NysDiagPP
      * :XDiag
      * :GirardHutchinsonShift
      * :RSVD
      * :AdaptiveDiagPP
  * StoppingCriterion: How to terminate, possible options

      * doubling: Use doubling strategy and terminate when the relative error estimate is below a threshold eps, required parameter

          * queries_start: number of queries to start with
          * eps: bound for the relative error estimate
          * Note: has only been implemented with :GirardHutchinson and :DiagPP, other methods will be added with future releases
      * queries: terminate when the maximum number of queries to A is reacher

          * maxqueries: maximum number of queries to A
      * adaptive: Using an epsilon delta estimator with :AdaptiveDiagPP

          * epsdelta: parameters (epsilon,delta) for an epsilon-delta estimator
          * maxiter: maximum iterations
  * distribution: Select the distribution from which the random vectors are drawn, inbuilt options are

      * :Rademacher
      * :Gaussion
      * :custom, in this case provide a matrix with the test vectors as columns

          * O: matrix with the test vectors as columns
