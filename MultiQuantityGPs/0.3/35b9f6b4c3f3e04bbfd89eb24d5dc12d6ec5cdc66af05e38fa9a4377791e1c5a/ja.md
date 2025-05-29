```julia
struct NamedTuple{(:x, :y), Tuple{Tuple{Vector{Float64}, Int64}, Float64}}
```

ノイズを含むサンプル測定の型、測定の平均と標準偏差
