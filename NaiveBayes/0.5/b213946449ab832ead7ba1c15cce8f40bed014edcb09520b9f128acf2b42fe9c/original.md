```
fit(m::HybridNB, f_c::Vector{Vector{Float64}}, f_d::Vector{Vector{Int64}}, labels::Vector{Int64})
```

Train NB model with discrete and continuous features by estimating P(x⃗|c)
