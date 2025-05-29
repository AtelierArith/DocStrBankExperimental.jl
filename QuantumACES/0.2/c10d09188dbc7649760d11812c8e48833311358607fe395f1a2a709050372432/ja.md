```
get_round_error(round_params::Vector{Float64})
get_round_error(round_params::Vector{Float64}, round_params_cov::Matrix{Float64})
```

`round_params`から決定されたラウンドごとの誤差と、共分散行列`round_params_cov`が提供された場合はその標準誤差を返します。
