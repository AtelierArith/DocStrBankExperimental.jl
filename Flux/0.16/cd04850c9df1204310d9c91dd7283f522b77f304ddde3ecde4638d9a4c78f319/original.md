```
lecun_normal([rng], size...) -> Array
lecun_normal([rng]; kw...) -> Function
```

Return an `Array{Float32}` of the given `size` containing random numbers drawn from a truncated normal distribution centered on 0 with stddev `sqrt(1 / fan_in)`, where `fan_in` is the number of input units  in the weight tensor.

# Examples

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> using Statistics

julia> round(std(Flux.lecun_normal(10, 1000)), digits=3)
0.032f0

julia> round(std(Flux.lecun_normal(1000, 10)), digits=3)
0.32f0

julia> round(std(Flux.lecun_normal(1000, 1000)), digits=3)
0.032f0

julia> Dense(10 => 1000, selu; init = Flux.lecun_normal())
Dense(10 => 1000, selu)  # 11_000 parameters

julia> round(std(ans.weight), digits=3)
0.313f0
```

# References

[1] Lecun, Yann, et al. "Efficient backprop." Neural networks: Tricks of the trade. Springer, Berlin, Heidelberg, 2012. 9-48.
