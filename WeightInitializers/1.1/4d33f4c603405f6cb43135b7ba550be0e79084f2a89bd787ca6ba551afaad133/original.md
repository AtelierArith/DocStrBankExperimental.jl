```
truncated_normal([::AbstractRNG=Utils.default_rng()], [T=Float32], size...; mean = 0,
    std = 1, lo = -2, hi = 2) -> AbstractArray{T, length(size)}
```

Return an `AbstractArray{T}` of the given `size` where each element is drawn from a truncated normal distribution. The numbers are distributed like `filter(x -> lo ≤ x ≤ hi, mean .+ std .* randn(100))`.
