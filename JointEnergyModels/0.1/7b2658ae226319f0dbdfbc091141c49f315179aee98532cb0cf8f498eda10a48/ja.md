```
ConditionalSampler(
    X::AbstractArray, y::AbstractArray;
    batch_size::Int,
    max_len::Int=10000, prob_buffer::AbstractFloat=0.95
)
```

`ConditionalSampler` の外部コンストラクタ。
