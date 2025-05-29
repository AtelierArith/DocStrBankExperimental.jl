```
mutable struct KPMExpansion{T<:AbstractFloat, Tfft<:FFTW.r2rFFTWPlan}
```

A type to represent the Chebyshev polynomial expansion used in the KPM algorithm.

# Fields

  * `M::Int`: Order of the Chebyshev polynomial expansion.
  * `bounds::NTuple{2,T}`: Bounds on eigenspectrum in the KPM algorithm.
  * `buf::Vector{T}`: The first `M` elements of this vector of the Chebyshev expansion coefficients.
  * `r2rplan::Tfft`: Plan for performing DCT to efficiently calculate the Chebyshev expansion coefficients via Chebyshev-Gauss quadrature.
