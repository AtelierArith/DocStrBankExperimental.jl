```
fit(m::HybridNB, f_c::Vector{Vector{Float64}}, f_d::Vector{Vector{Int64}}, labels::Vector{Int64})
```

離散および連続特徴を持つNBモデルをP(x⃗|c)を推定することで訓練します。
