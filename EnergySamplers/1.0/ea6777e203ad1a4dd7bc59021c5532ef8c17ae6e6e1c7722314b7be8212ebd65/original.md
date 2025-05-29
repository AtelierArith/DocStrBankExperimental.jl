```
UnconditionalSampler(
    𝒟x::Distribution,
    𝒟y::Union{Distribution,Nothing};
    input_size::Dims,
    batch_size::Int = 1,
    max_len::Int = 10000,
    prob_buffer::AbstractFloat = 0.95,
)
```

Outer constructor for `UnonditionalSampler`.
