```
randn32([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float32, length(size)}
```

与えられた `size` の `AbstractArray{Float32}` を返し、標準正規分布からのランダムな数値を含みます。
