```
peak_factor(Dex::U, m0::V, rvt::RandomVibrationParameters; glxi::Vector{Float64}=xn31i, glwi::Vector{Float64}=wn31i, nodes::Int=length(glxi)) where {U<:Real}
```

ピークファクター u*max / u*rms は、採用されたアプローチを決定するために `pf_method` のスイッチを使用します。`pf_method` は現在次のいずれかです： 	- `:CL56` カートライト・ロングエット・ヒギンズ (1956) 	- `:DK80` デア・キュレギアン (1980)、ヴァンマルケ (1975) に基づく

デフォルトは `:DK80` です。
