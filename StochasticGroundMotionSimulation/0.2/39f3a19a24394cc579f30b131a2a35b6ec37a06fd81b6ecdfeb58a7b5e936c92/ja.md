```
rvt_response_spectrum!(Sa::Vector{U}, period::Vector{V}, m::S, r_ps::T, fas::FourierParameters, rvt::RandomVibrationParameters) where {S<:Real,T<:Real,U<:Real,V<:Float64}
```

ベクトルの周期 `period` と指定されたシナリオに対するインプレース応答スペクトル（単位は $g$）。

各スペクトルオルディネートは次の式を使用して計算されます：

$$
S_a = \psi \sqrt{\frac{m_0}{D_{rms}}}
$$

ここで、$\psi$ は `peak_factor` から計算されたピークファクター、$m_0$ は `spectral_moment` からのゼロ次スペクトルモーメント、$D_{rms}$ は `rms_duration` から計算されたRMS持続時間です。さまざまな項はすべてオシレーターの周期の関数です。

関連情報: [`rvt_response_spectral_ordinate`](@ref), [`rvt_response_spectrum!`](@ref)
