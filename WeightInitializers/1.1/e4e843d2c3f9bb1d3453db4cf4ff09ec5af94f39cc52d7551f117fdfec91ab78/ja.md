```
zeros64([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float64, length(size)}
```

与えられた `size` のゼロの AbstractArray を含む `AbstractArray{Float64}` を返します。
