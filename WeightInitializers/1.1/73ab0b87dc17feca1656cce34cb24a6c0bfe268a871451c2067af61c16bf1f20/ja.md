```
randn64([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float64, length(size)}
```

与えられた `size` の標準正規分布からのランダム数を含む `AbstractArray{Float64}` を返します。
