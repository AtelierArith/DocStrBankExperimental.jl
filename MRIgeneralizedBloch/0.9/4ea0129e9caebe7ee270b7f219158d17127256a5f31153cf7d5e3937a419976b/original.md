```
graham_saturation_rate_single_frequency(lineshape, ω1, TRF, Δω)
```

Calculate saturation rate (in units of 1/s) according to Graham's single frequency approximation.

# Arguments

  * `lineshape::Function`: as a function of ω₀ (in rad/s). Supply, e.g., the anonymous function `ω₀ -> lineshape_superlorentzian(ω₀, T2s)`. Note that the integral over the lineshape has to be 1.
  * `ω1::Function`: ω1 in rad/s as a function of time (in units of s) where the puls shape is defined for t ∈ [0,TRF]
  * `TRF::Real`: duration of the RF pulse in s
  * `Δω::Real`: offset frequency in rad/s

# Examples

```jldoctest
julia> using SpecialFunctions

julia> T2s = 10e-6;

julia> α = π;

julia> TRF = 100e-6;

julia> NSideLobes = 1;

julia> ω1(t) = sinc(2(NSideLobes+1) * t/TRF - (NSideLobes+1)) * α / (sinint((NSideLobes+1)π) * TRF/π / (NSideLobes+1));

julia> Δω = 200;

julia> graham_saturation_rate_single_frequency(ω₀ -> lineshape_superlorentzian(ω₀, T2s), ω1, TRF, Δω)
419969.3376658947
```
