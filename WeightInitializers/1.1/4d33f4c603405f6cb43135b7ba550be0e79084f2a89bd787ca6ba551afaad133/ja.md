```
truncated_normal([::AbstractRNG=Utils.default_rng()], [T=Float32], size...; mean = 0,
    std = 1, lo = -2, hi = 2) -> AbstractArray{T, length(size)}
```

与えられた `size` の `AbstractArray{T}` を返します。各要素は切断正規分布から抽出されます。数値は `filter(x -> lo ≤ x ≤ hi, mean .+ std .* randn(100))` のように分布します。
