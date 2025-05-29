```julia
struct EKMDefuzzifier <: FuzzyLogic.Type2Defuzzifier
```

Enhanced Karnik-Mendel type-reduction/defuzzification algorithm for Type-2 fuzzy systems.

### Parameters

  * `N::Int64`: number of subintervals for integration, default 100.
  * `maxiter::Int64`: maximum number of iterations, default 100.

# Extended help

The algorithm was introduced in

  * Wu, D. and J.M. Mendel, "Enhanced Karnik-Mendel algorithms," IEEE Transactions on Fuzzy Systems, vol. 17, pp. 923-934. (2009)
