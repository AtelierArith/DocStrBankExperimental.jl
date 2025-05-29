```
fit_round_error(rounds_set::Vector{Int}, rounds_memory_errors::Vector{Float64}, rounds_memory_errors_sem::Vector{Float64}; return_cov::Bool = false)
```

`rounds_set`のラウンドにわたるメモリエラー`rounds_memory_errors`とその平均の標準誤差`rounds_memory_errors_sem`から加重最小二乗法でフィッティングされた[`round_exponential_model`](@ref)のパラメータを返します。
