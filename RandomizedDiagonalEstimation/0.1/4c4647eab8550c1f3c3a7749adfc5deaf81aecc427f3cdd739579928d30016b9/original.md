```
function EstimateMoMDiagonal(A::Matrix{Float64},Algorithm::Symbol, StoppingCriterion::Symbol, distribution::Symbol, ngroups::Int, groupsize::Int, normalizationParam::Bool=true, parallelizationParam::Bool=false ;maxqueries::Int,O=nothing)
```

Function that computes a randomized estimate of the diagonal of a matrix using the median of means principle

Input:

  * A: Matrix to estimate the diagonal of
  * Algorithm: Choose which diagonal estimator is used, options are

      * :GirardHutchinson
      * :DiagPP
      * :NysDiagPP
      * :XDiag
      * :XNysDiag
      * :GirardHutchinsonShift
      * :RSVD
      * :AdaptiveDiagPP
  * StoppingCriterion: How to terminate, possible options

      * queries: terminate when the maximum number of queries to A is reacher

          * maxqueries: maximum number of queries to A
      * Note potential further stopping criteria will be added in future versions
  * distribution: Select the distribution from which the random vectors are drawn, inbuilt options are

      * :Rademacher
      * :Gaussion
      * :custom, in this case provide a matrix with the test vectors as columns

          * O: matrix with the test vectors as columns
  * ngroups: Number of groups for the Median of Means estimator
  * groupsize: Groupsize for the Median of Means estimator
