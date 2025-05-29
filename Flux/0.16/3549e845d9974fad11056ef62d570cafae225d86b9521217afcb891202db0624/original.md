```
glorot_uniform([rng], size...; gain = 1) -> Array
glorot_uniform([rng]; kw...) -> Function
```

Return an `Array{Float32}` of the given `size` containing random numbers drawn from a uniform distribution on the interval $[-x, x]$, where `x = gain * sqrt(6 / (fan_in + fan_out))`.

This method is described in [1] and also known as Xavier initialization.

# Examples

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> Flux.glorot_uniform(3, 4) |> summary
"3×4 Matrix{Float32}"

julia> round.(extrema(Flux.glorot_uniform(10, 100)), digits=3)
(-0.233f0, 0.233f0)

julia> round.(extrema(Flux.glorot_uniform(100, 10)), digits=3)
(-0.234f0, 0.233f0)

julia> round.(extrema(Flux.glorot_uniform(100, 100)), digits=3)
(-0.173f0, 0.173f0)

julia> Dense(3 => 2, tanh; init = Flux.glorot_uniform(MersenneTwister(1)))
Dense(3 => 2, tanh)  # 8 parameters

julia> ans.bias
2-element Vector{Float32}:
 0.0
 0.0
```

# References

[1] Glorot, Xavier, and Yoshua Bengio. "Understanding the difficulty of training deep feedforward neural networks." *Proceedings of the thirteenth international conference on artificial intelligence and statistics*. 2010.
