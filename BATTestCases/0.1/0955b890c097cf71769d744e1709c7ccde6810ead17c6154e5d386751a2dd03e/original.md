```
struct GaussianShell <: Distribution{Multivariate,Continuous}
```

*Experimental feature, not part of stable public API.*

Gaussian Shell (see [Caldwell et al.](https://arxiv.org/abs/1808.08051) for definition).

Constructors:

  * `GaussianShell(; r::Real=5, w::Real=2, n::Integer=2)`

Fields:

  * `r::Real`: The radius of the Gaussian shell distribution.
  * `w::Real`: Variance of the Gaussian shell distribution
  * `n::Int64`: Number of dimensions
  * `c::AbstractVector{<:Real}`
  * `lognorm::AbstractFloat`

!!! note
    Fields `c` and `lognorm` are considered internal and subject to change without deprecation.

