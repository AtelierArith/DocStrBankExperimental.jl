```
kaiming_uniform([rng], size...; gain = √2) -> Array
kaiming_uniform([rng]; kw...) -> Function
```

与えられた `size` の `Array{Float32}` を返し、`[-x, x]` の区間から引かれた一様分布のランダム数を含みます。ここで、`x = gain * sqrt(3/fan_in)` であり、[`nfan`](@ref Flux.nfan) を使用します。

このメソッドは [1] で説明されており、He初期化としても知られています。

# 例

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> round.(extrema(Flux.kaiming_uniform(100, 10)), digits=3)
(-0.774f0, 0.773f0)

julia> round.(extrema(Flux.kaiming_uniform(10, 100)), digits=3)
(-0.243f0, 0.245f0)

julia> round.(extrema(Flux.kaiming_uniform(100, 100)), digits=3)
(-0.245f0, 0.245f0)
```

# 参考文献

[1] He, Kaiming, et al. "Delving deep into rectifiers: Surpassing human-level performance on imagenet classification." *Proceedings of the IEEE international conference on computer vision*. 2015.
