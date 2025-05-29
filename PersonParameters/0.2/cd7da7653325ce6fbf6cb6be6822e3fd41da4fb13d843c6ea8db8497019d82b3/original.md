```julia
struct WLE{T<:Roots.AbstractSecantMethod} <: PersonParameters.PersonParameterAlgorithm
```

Warm's weighted likelihood estimation for person parameters of item response models.

# References

  * Warm, T. A. (1989). Weighted likelihood estimation of ability in item response theory. Psychometrika, 54, 427-450. doi: 10.1007/BF02294627
