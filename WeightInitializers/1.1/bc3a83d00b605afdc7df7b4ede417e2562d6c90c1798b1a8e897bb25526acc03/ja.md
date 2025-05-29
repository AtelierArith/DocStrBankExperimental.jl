```
zeros16([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float16, length(size)}
```

与えられた `size` のゼロの AbstractArray を含む `AbstractArray{Float16}` を返します。
