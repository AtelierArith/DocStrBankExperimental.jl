```
ns_dwt(x, wt, [L])
```

Nonstandard wavelet transform on 1D signals.

# Arguments

  * `x::AbstractVector{T} where T<:AbstractFloat`: 1D signal of length $2^J$.
  * `wt::OrthoFilter`: Type of wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of decomposition levels.

# Returns

  * `nxw::Vector{T}`: Nonstandard wavelet transform of `x` of length $2^{J+1}$.

# Examples

```jldoctest
julia> using Wavelets, WaveletsExt; import Random: seed!

julia> seed!(1234); x = randn(4)
4-element Vector{Float64}:
 -0.3597289068234817
  1.0872084924285859
 -0.4195896169388487
  0.7189099374659392

julia> wt = wavelet(WT.haar);

julia> nxw = ns_dwt(x, wt)      # Nonstandard transform
8-element Vector{Float64}:
  0.0
  0.0
  0.5133999530660974
 -0.2140796325390069
  0.5144057481561487
  0.21165142839163664
  1.0231392469635638
  0.8050407552974883

julia> x̂ = ns_idwt(nxw, wt)     # Nonstandard inverse transform
4-element Vector{Float64}:
  0.004010885979070622
  1.4509482852311382
 -0.2699294566753035
  0.8685700977294846

julia> x ≈ x̂                    # Unlike standard dwt, x ≠ x̂
false
```

**See also:** [`nonstd_wavemult`](@ref), [`mat2sparseform_nonstd`](@ref), [`ns_idwt`](@ref), [`ndyad`](@ref)
