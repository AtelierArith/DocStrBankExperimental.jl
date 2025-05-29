```
bspec(times, dat, W, K, beta, nz, Ftest)
```

Computes the Bronez spectrum of an unequally-spaced time series

...

# Positional Arguments

  * `times::Vector{T} where T<: Number`: the vector containing the times
  * `dat::Vector{T} where T<:Number`: the vector containing the time series
  * `W::Float64`: bandwidth of estimate
  * `K::Int64`: number of slepian tapers, must be <= 2*NW
  * `beta::Float64`: estimated process bandwidth (aka Nyquist rate)
  * `nz::Union{Float64,Int64} = length(t)`: Number of frequencies
  * `Ftest::Bool = false`: Whether to compute the F-test or not

...

...

# Outputs

  * MTSpectrum struct containing the Bronez spectrum

...

...

# Example usage

```<julia>
N = 256
t = collect(1:N).^(1.05)
W = 0.008
K = 5
x = randn(N)
bet = 0.5 / (last(t) / (N-1))
M = 2*N
S = bspec(t, x, W, K, bet, nz, true)
```

...

See also: [`multispec`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref), [`gpss`](@ref)
