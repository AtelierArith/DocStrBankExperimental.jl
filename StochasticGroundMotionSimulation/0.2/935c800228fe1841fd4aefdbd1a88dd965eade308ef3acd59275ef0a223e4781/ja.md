```
peak_factor(m::S, r_ps::T, fas::FourierParameters, sdof::Oscillator, rvt::RandomVibrationParameters; glxi::Vector{Float64}=xn31i, glwi::Vector{Float64}=wn31i, nodes::Int=length(glxi)) where {S<:Real,T<:Real}
```

ピークファクター $u_{max} / u_{rms}$ は、採用されたアプローチを決定するために `pf_method` のスイッチを使用します。`rvt.pf_method` は現在次のいずれかです： 	- `:CL56` カートライト・ロングエット・ヒギンズ (1956) 	- `:DK80` デル・キュレギアン (1980)、ヴァンマルケ (1975) に基づく

デフォルトは `:DK80` です。
