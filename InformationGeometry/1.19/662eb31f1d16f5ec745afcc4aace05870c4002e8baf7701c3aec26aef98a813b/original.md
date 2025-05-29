```
SumExponentialsModel(x::Union{Number,AbstractVector{<:Number}}, θ::AbstractVector{<:Number})
```

$$
y(x,θ) = θ_{n+1} + exp(x_1 * θ_1) + exp(x_2 * θ_2) + ... + exp(x_n * θ_n)
$$
