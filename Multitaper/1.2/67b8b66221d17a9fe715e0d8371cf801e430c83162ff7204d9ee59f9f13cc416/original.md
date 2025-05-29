```
bspec(time, dat1, dat2, W, K, bet, nz; <keyword arguments>)
```

Computes the Bronez coherence or cross-spectrum of two unequally-spaced time series

...

# Positional Arguments

  * `time::Vector{T} where T<:Number`: the vector containing the times
  * `dat1::Union{Vector{P}, EigenCoefficient} where P<:Number`: the vector containing the first time series
  * `dat2::Union{Vector{P}, EigenCoefficient} where P<:Number`: the vector containing the second time series
  * `W::Float64`: bandwidth of estimate
  * `K::Int64`: number of slepian tapers, must be <= 2*NW
  * `bet::Float64`: Nyquist frequency
  * `nz::Union{Float64,Int64} = length(t)`: Number of frequencies

# Keyword Arguments

  * `outp::Symb = :coh`: Output, either `:cross` for cross spectrum or `:coh` (default)
  * `params::Union{MTParameters,Nothing} = nothing`: parameters struct, important when x,y are EigenCoefficients
  * `Ftest::Bool = false`: Whether to compute the F-test or not

...

...

# Outputs

  * MTCoherence containing the Bronez coherence

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
S = bspec(t, x, y, W, K, M, beta)
```

...

See also: [`multispec`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref), [`gpss`](@ref)
