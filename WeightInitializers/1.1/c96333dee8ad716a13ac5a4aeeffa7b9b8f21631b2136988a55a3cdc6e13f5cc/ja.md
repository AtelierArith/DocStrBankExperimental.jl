```
onesC32([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{ComplexF32, length(size)}
```

与えられた `size` の `AbstractArray` のすべての要素が1の `AbstractArray{ComplexF32}` を返します。
