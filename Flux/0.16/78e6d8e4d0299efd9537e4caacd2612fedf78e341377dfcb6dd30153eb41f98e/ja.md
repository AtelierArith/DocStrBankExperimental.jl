```
kaiming_normal([rng], size...; gain = √2) -> Array
kaiming_normal([rng]; kw...) -> Function
```

指定された `size` の `Array{Float32}` を返し、標準偏差 `gain / sqrt(fan_in)` の正規分布から取得したランダムな数値を含みます。 [`nfan`](@ref Flux.nfan) を使用します。

このメソッドは [1] で説明されており、He初期化としても知られています。

# 例

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> using Statistics

julia> round(std(Flux.kaiming_normal(10, 1000)), digits=3)
0.044f0

julia> round(std(Flux.kaiming_normal(1000, 10)), digits=3)
0.45f0

julia> round(std(Flux.kaiming_normal(1000, 1000)), digits=3)
0.045f0
```

# 参考文献

[1] He, Kaiming, et al. "Delving deep into rectifiers: Surpassing human-level performance on imagenet classification." *Proceedings of the IEEE international conference on computer vision*. 2015.
