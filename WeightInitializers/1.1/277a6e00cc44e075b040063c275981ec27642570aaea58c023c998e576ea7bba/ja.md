```
onesC64([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{ComplexF64, length(size)}
```

与えられた `size` の `AbstractArray` を含む `AbstractArray{ComplexF64}` を返します。
