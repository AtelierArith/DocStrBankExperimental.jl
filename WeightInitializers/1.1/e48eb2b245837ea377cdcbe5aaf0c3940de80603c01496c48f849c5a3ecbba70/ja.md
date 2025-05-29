```
rand64([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float64, length(size)}
```

与えられた `size` の `AbstractArray{Float64}` を返し、均一分布からのランダムな数値を含みます。
