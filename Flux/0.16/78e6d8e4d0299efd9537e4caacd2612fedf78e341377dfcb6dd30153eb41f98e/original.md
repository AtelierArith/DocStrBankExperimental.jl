```
kaiming_normal([rng], size...; gain = √2) -> Array
kaiming_normal([rng]; kw...) -> Function
```

Return an `Array{Float32}` of the given `size` containing random numbers taken from a normal distribution standard deviation `gain / sqrt(fan_in)`, using [`nfan`](@ref Flux.nfan).

This method is described in [1] and also known as He initialization.

# Examples

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> using Statistics

julia> round(std(Flux.kaiming_normal(10, 1000)), digits=3)
0.044f0

julia> round(std(Flux.kaiming_normal(1000, 10)), digits=3)
0.45f0

julia> round(std(Flux.kaiming_normal(1000, 1000)), digits=3)
0.045f0
```

# References

[1] He, Kaiming, et al. "Delving deep into rectifiers: Surpassing human-level performance on imagenet classification." *Proceedings of the IEEE international conference on computer vision*. 2015.
