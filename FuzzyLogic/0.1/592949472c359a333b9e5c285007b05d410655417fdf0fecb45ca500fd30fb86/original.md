```julia
struct KarnikMendelDefuzzifier <: FuzzyLogic.Type2Defuzzifier
```

Karnik-Mendel type-reduction/defuzzification algorithm for Type-2 fuzzy systems.

### Parameters

  * `N::Int64`: number of subintervals for integration, default 100.
  * `maxiter::Int64`: maximum number of iterations, default 100.
  * `atol::Float64`: absolute tolerance for stopping iterations

# Extended help

The algorithm was introduced in

  * Karnik, Nilesh N., and Jerry M. Mendel. ‘Centroid of a Type-2 Fuzzy Set’. Information Sciences 132, no. 1–4 (February 2001): 195–220
