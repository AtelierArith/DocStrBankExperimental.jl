```
fit_dist_error(dist_set::Vector{Int}, dist_memory_errors::Vector{Float64}, dist_memory_errors_sem::Vector{Float64}; return_cov::Bool = false)
```

メモリエラー `dist_memory_errors` とそれらの平均の標準誤差 `dist_memory_errors_sem` を用いて、重み付き最小二乗法でフィッティングされた [`dist_linear_model`](@ref) のパラメータを返します。フィッティングは対数空間で行われるため、元のパラメータをフィットさせるには、[`dist_linear_model`](@ref) の出力を指数化してください。
