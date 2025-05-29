```
randnC16([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{ComplexF16, length(size)}
```

与えられた `size` の `AbstractArray{ComplexF16}` を返し、標準正規分布からのランダムな数値を含みます。
