```julia
struct LeftMaximumDefuzzifier <: FuzzyLogic.AbstractDefuzzifier
```

Left maximum defuzzifier. Returns the smallest value in the domain for which the membership function reaches its maximum.

### Parameters

  * `N::Int64`: number of subintervals, default 100.
  * `tol::Float64`: absolute tolerance to determine if a value is maximum, default `eps(Float64)`.
