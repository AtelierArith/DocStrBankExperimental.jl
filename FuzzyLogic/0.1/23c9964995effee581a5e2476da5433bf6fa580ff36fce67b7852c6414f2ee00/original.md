```julia
struct EIASCDefuzzifier <: FuzzyLogic.Type2Defuzzifier
```

Defuzzifier for type-2 inference systems using Iterative Algorithm with Stopping Condition (IASC).

### PARAMETERS

  * `N::Int64`: number of subintervals for integration, default 100.

# Extended help

The algorithm was introduced in

  * Wu, D. and M. Nie, "Comparison and practical implementations of type-reduction algorithms for type-2 fuzzy sets and systems," Proceedings of FUZZ-IEEE, pp. 2131-2138 (2011)
