```julia
struct NamedTuple{(:lower, :upper), Tuple{Vector{Float64}, Vector{Float64}}}
```

領域の境界。下限と上限から成り、それぞれ浮動小数点値のリストです。
