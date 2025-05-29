```
glorot_normal([rng], size...; gain = 1) -> Array
glorot_normal([rng]; kw...) -> Function
```

Return an `Array{Float32}` of the given `size` containing random numbers drawn from a normal distribution with standard deviation `gain * sqrt(2 / (fan_in + fan_out))`, using [`nfan`](@ref Flux.nfan).

This method is described in [1] and also known as Xavier initialization.

# Examples

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> using Statistics

julia> round(std(Flux.glorot_normal(10, 1000)), digits=3)
0.044f0

julia> round(std(Flux.glorot_normal(1000, 10)), digits=3)
0.045f0

julia> round(std(Flux.glorot_normal(1000, 1000)), digits=3)
0.032f0

julia> Dense(10 => 1000, tanh; init = Flux.glorot_normal(gain=100))
Dense(10 => 1000, tanh)  # 11_000 parameters

julia> round(std(ans.weight), sigdigits=3)
4.45f0
```

# References

[1] Glorot, Xavier, and Yoshua Bengio. "Understanding the difficulty of training deep feedforward neural networks." *Proceedings of the thirteenth international conference on artificial intelligence and statistics*. 2010.
