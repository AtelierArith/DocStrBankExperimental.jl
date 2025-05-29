```
get_peak_line_amps_percent(m::JuMP.AbstractModel, p::Inputs{MultiPhase})
```

A `Dict{String, Float64}` with edge keys and peak percent line amps (peak over all time steps)

Estimating the line amps as $|(V_i - V_j) / Z|$ where we use the approximation: $|V_i - V_j| \approx r_{ij} P_{ij} + x_{ij} Q_{ij}$
