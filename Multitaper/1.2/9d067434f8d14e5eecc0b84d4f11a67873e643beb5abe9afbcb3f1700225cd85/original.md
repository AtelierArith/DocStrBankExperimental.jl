```
bspec(time, dat, W, K, bet, nz; <keyword arguments>)
```

Computes the Bronez spectra and coherences of p unequally-spaced time series

...

# Positional Arguments

  * `time::Vector{T} where T<:Number`: the vector containing the times
  * `dat::Matrix{Vector{P}} where T<:Number`: the matrix containing the time series in its columns
  * `W::Float64`: bandwidth of estimate
  * `K::Int64`: number of slepian tapers, must be <= 2*NW
  * `bet::Float64`: Nyquist frequency
  * `nz::Union{Float64,Int64} = length(t)`: Number of frequencies

# Keyword Arguments

  * `outp::Symb = :coh`: Output, either `:cross` for cross spectrum or `:coh` (default)
  * `Ftest::Bool = false`: Whether to compute the F-test or not

...

...

# Outputs

  * tuple(Vector{MTSpectrum},Matrix{MTCoherence},Nothing) containing the Bronez spectra and coherences

...

...

# Example usage

```<julia>
N = 256
t = collect(1:N).^(1.05)
W = 0.008
K = 5
x = randn(N)
y = randn(N) # Incoherent
M = 2*N
beta = 0.5
S = bspec(t, hcat(x, y), W, K, beta, M, outp = :coh, Ftest = true)
```

...

See also: [`multispec`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref), [`gpss`](@ref)
