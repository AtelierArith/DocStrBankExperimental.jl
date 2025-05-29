```Julia
stefan(U::UnitSystem) = τ^5/𝟐^4*boltzmann(U)^4/(𝟑*𝟓*planck(U)^3*lightspeed(U)^2)
```

ステファン・ボルツマンの比例定数 `σ` の黒体放射 (W⋅m⁻²⋅K⁻⁴ または ?⋅ft⁻²⋅°R⁻⁴)。

```Julia
julia> stefan(SI2019) # W⋅m⁻²⋅K⁻⁴
5.6703744191844314e-8

julia> stefan(Metric) # W⋅m⁻²⋅K⁻⁴
5.670374411387805e-8

julia> stefan(Conventional) # W⋅m⁻²⋅K⁻⁴
5.6703733026225384e-8

julia> stefan(CODATA) # W⋅m⁻²⋅K⁻⁴
5.6703666286764085e-8

julia> stefan(Metric)*day(Metric)/(calorie(Metric)*100^2) # cal⋅cm⁻²⋅day⁻¹⋅K⁻⁴
0.0011701721682605046

julia> stefan(English) # lb⋅s⁻¹⋅ft⁻³⋅°R⁻⁴
3.701265696325433e-10
```
