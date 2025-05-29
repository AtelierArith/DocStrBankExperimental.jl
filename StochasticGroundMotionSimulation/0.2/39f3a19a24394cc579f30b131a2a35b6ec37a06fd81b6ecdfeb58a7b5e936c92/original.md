```
rvt_response_spectrum!(Sa::Vector{U}, period::Vector{V}, m::S, r_ps::T, fas::FourierParameters, rvt::RandomVibrationParameters) where {S<:Real,T<:Real,U<:Real,V<:Float64}
```

In-place response spectrum (units of $g$) for the vector of periods `period` and the specified scenario.

Each spectral ordinate is computed using the expression:

$$
S_a = \psi \sqrt{\frac{m_0}{D_{rms}}}
$$

where $\psi$ is the peak factor computed from `peak_factor`, $m_0$ is the zeroth order spectral moment from `spectral_moment`, and $D_{rms}$ is the RMS duration computed from `rms_duration`. The various terms are all functions of the oscillator period.

See also: [`rvt_response_spectral_ordinate`](@ref), [`rvt_response_spectrum!`](@ref)
