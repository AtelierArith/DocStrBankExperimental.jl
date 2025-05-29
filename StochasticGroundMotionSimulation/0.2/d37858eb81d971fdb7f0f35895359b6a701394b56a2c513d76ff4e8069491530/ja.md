```
rvt_response_spectral_ordinate(m::S, r_ps::T, fas::FourierParameters, sdof::Oscillator, rvt::RandomVibrationParameters; glxi::Vector{Float64}=xn31i, glwi::Vector{Float64}=wn31i) where {S<:Real,T<:Real}
```

指定されたシナリオの応答スペクトルオルディネート（単位は $g$）。

スペクトルオルディネートは次の式を使用して計算されます：

$$
S_a = \psi \sqrt{\frac{m_0}{D_{rms}}}
$$

ここで、$\psi$ は `peak_factor` から計算されたピークファクター、$m_0$ は `spectral_moment` からのゼロ次スペクトルモーメント、$D_{rms}$ は `rms_duration` から計算されたRMS持続時間です。

参照： [`rvt_response_spectral_ordinate`](@ref), [`rvt_response_spectrum`](@ref), [`rvt_response_spectrum!`](@ref)
