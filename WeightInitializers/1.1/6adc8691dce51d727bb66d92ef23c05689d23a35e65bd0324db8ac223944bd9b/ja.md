```
zeros32([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float32, length(size)}
```

指定された `size` のゼロの AbstractArray を含む `AbstractArray{Float32}` を返します。
