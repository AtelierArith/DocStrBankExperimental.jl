```
get_dist_error(dist_params::Vector{Float64})
get_dist_error(dist_params::Vector{Float64}, dist_params_cov::Matrix{Float64})
```

距離が2増加するにつれてコード内のエラー率の変化を、`dist_params`から決定されたエラー抑制係数を返し、共分散行列`dist_params_cov`が提供されている場合はその標準誤差も返します。
