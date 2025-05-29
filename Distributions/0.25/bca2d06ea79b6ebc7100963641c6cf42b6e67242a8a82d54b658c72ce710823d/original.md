```
Soliton(K::Integer, M::Integer, δ::Real, atol::Real=0) <: Distribution{Univariate, Discrete}
```

The Robust Soliton distribution of length `K`, mode `M` (i.e., the location of the robust component spike), peeling process failure probability `δ`, and minimum non-zero probability mass `atol`. More specifically, degrees `i` for which `pdf(Ω, i)<atol` are set to `0`. Letting `atol=0` yields the regular robust Soliton distribution.

```julia
Soliton(K, M, δ)        # Robust Soliton distribution (with atol=0)
Soliton(K, M, δ, atol)  # Robust Soliton distribution with minimum non-zero probability mass atol

params(Ω)               # Get the parameters ,i.e., (K, M, δ, atol)
degrees(Ω)              # Return a vector composed of the degrees with non-zero probability mass
pdf(Ω, i)               # Evaluate the pdf at i
cdf(Ω, i)               # Evaluate the pdf at i
rand(Ω)                 # Sample from Ω
rand(Ω, n)              # Draw n samples from Ω
```

External links:

  * [Soliton distribution on Wikipedia](https://en.wikipedia.org/wiki/Soliton_distribution)
