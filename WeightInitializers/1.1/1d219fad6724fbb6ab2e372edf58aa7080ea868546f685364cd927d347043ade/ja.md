```
ones32([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float32, length(size)}
```

指定された `size` の AbstractArray のすべての要素が 1 の `AbstractArray{Float32}` を返します。
