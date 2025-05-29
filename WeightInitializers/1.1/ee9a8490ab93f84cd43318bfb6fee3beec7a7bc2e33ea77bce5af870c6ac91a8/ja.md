```
rand16([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float16, length(size)}
```

与えられた `size` の `AbstractArray{Float16}` を返し、均一分布からのランダムな数値を含みます。
