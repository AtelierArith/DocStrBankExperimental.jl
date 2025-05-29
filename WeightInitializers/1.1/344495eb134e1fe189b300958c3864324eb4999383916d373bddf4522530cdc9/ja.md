```
randn16([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{Float16, length(size)}
```

与えられた `size` の標準正規分布からのランダムな数値を含む `AbstractArray{Float16}` を返します。
