```
kaiming_uniform([rng], size...; gain = √2) -> Array
kaiming_uniform([rng]; kw...) -> Function
```

Return an `Array{Float32}` of the given `size` containing random numbers drawn from a uniform distribution on the interval `[-x, x]`, where `x = gain * sqrt(3/fan_in)` using [`nfan`](@ref Flux.nfan).

This method is described in [1] and also known as He initialization.

# Examples

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> round.(extrema(Flux.kaiming_uniform(100, 10)), digits=3)
(-0.774f0, 0.773f0)

julia> round.(extrema(Flux.kaiming_uniform(10, 100)), digits=3)
(-0.243f0, 0.245f0)

julia> round.(extrema(Flux.kaiming_uniform(100, 100)), digits=3)
(-0.245f0, 0.245f0)
```

# References

[1] He, Kaiming, et al. "Delving deep into rectifiers: Surpassing human-level performance on imagenet classification." *Proceedings of the IEEE international conference on computer vision*. 2015.
