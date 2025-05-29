```
PolyaGammaHybridSampler(b::Real, z::Real, [method::PGSamplingMethod])
```

A sampler for the Polya-Gamma distribution using a hybrid of the saddlepoint approximation, the Devroye method,  the normal approximation, and the sum of gammas approximation, each of which are discussed in  Windle et al. (2014) – see README.md for details.

# Arguments

  * `b::Real`: The shape parameter of the Polya-Gamma distribution. Must be positive.
  * `z::Real`: The exponential tilting parameter of the Polya-Gamma distribution.
  * `method::PGSamplingMethod : An Enum object specifying the method used to sample from the Polya-Gamma distribution.    Must be one of`DEVROYE`,`SADDLEPOINT`,`NORMALAPPROX`,`GAMMASUM`, or`DEVROYEPLUSGAMMASUM`.   If omitted, the method is chosen automatically based on the value of`b`.

# Returns

  * A `PolyaGammaHybridSampler` object which can be sampled using `rand` or `rand!`.

# Examples

```julia
julia> using PolyaGammaHybridSamplers
julia> s = PolyaGammaHybridSampler(1, 1.0)
julia> rand(s)
```

# Notes

  * Automatic selection criteria: 

      * `b > 170` -> `NORMALAPPROX`
      * `b >= 13` -> `SADDLEPOINT`
      * `b >= 1 && isinteger(b)` -> `DEVROYE`
      * `b > 1 && !isinteger(b)` -> `DEVROYEPLUSGAMMASUM`
      * `b >= 0` -> `GAMMASUM`
      * `b = 0` -> degenerate distribution at 0
