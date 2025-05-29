```
get_peak_line_amps_percent(m::JuMP.AbstractModel, p::Inputs{MultiPhase})
```

エッジキーとピークパーセントラインアンプ（すべての時間ステップでのピーク）を持つ `Dict{String, Float64}`

ラインアンプを $|(V_i - V_j) / Z|$ として推定し、近似を使用します: $|V_i - V_j| \approx r_{ij} P_{ij} + x_{ij} Q_{ij}$
