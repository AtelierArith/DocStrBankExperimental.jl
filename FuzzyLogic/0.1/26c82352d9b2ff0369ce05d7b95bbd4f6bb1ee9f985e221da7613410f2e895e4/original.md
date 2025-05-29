```julia
struct IASCDefuzzifier <: FuzzyLogic.Type2Defuzzifier
```

Defuzzifier for type-2 inference systems using Iterative Algorithm with Stopping Condition (IASC).

### PARAMETERS

  * `N::Int64`: number of subintervals for integration, default 100.

# Extended help

The algorithm was introduced in

  * Duran, K., H. Bernal, and M. Melgarejo, "Improved iterative algorithm for computing the generalized centroid of an interval type-2 fuzzy set," Annual Meeting of the North American Fuzzy Information Processing Society, pp. 190-194. (2008)
