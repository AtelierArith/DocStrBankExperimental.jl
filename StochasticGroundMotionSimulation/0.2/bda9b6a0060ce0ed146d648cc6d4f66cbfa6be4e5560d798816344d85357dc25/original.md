```
rvt_response_spectral_ordinate(period::U, m::S, r_ps::T, fas::FourierParameters, rvt::RandomVibrationParameters; glxi::Vector{Float64}=xn31i, glwi::Vector{Float64}=wn31i) where {S<:Real,T<:Real,U<:Float64}
```

Response spectral ordinate (units of $g$) for the specified scenario.

The spectral ordinate is computed using the expression:

$$
S_a = \psi \sqrt{\frac{m_0}{D_{rms}}}
$$

where $\psi$ is the peak factor computed from `peak_factor`, $m_0$ is the zeroth order spectral moment from `spectral_moment`, and $D_{rms}$ is the RMS duration computed from `rms_duration`.

See also: [`rvt_response_spectral_ordinate`](@ref), [`rvt_response_spectrum`](@ref), [`rvt_response_spectrum!`](@ref)
