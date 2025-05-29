```
randC32([::AbstractRNG=Utils.default_rng()], size...;
    kwargs...) -> AbstractArray{ComplexF32, length(size)}
```

指定された `size` の `AbstractArray{ComplexF32}` を返し、均一分布からのランダムな数値を含みます。
