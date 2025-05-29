```
ARPWeighting{T<:AbstractFloat} <: AbstractMCMCWeightingScheme{T}
```

*Experimental feature, not part of stable public API.*

Sample weighting scheme suitable for accept/reject-based sampling algorithms (e.g. [`MetropolisHastings`](@ref)). Both accepted and rejected samples become part of the output, with a weight proportional to their original acceptance probability.

Constructors:

  * `ARPWeighting()`
