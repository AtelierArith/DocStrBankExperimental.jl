```julia
GetCount(Es::Vector{Float64}, mu::Float64, T::Float64, stat::Int64) --> Matrix{Float64}
```

エネルギーが化学ポテンシャルよりも低い場合は 1、そうでなければ 0 となる M[i, i] = θ(-(E^i(k)-μ)) のエントリを持つ対角行列を返す関数。
