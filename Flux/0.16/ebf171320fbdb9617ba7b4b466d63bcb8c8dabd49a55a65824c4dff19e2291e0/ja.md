```
glorot_normal([rng], size...; gain = 1) -> Array
glorot_normal([rng]; kw...) -> Function
```

与えられた `size` の `Array{Float32}` を返し、標準偏差 `gain * sqrt(2 / (fan_in + fan_out))` の正規分布から抽出されたランダムな数値を含みます。 [`nfan`](@ref Flux.nfan) を使用します。

このメソッドは [1] で説明されており、Xavier 初期化としても知られています。

# 例

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

# 参考文献

[1] Glorot, Xavier, and Yoshua Bengio. "Understanding the difficulty of training deep feedforward neural networks." *Proceedings of the thirteenth international conference on artificial intelligence and statistics*. 2010.
