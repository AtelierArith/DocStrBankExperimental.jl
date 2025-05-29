```
lecun_normal([rng], size...) -> Array
lecun_normal([rng]; kw...) -> Function
```

与えられた `size` の `Array{Float32}` を返し、0を中心とし、標準偏差 `sqrt(1 / fan_in)` の切断正規分布から抽出されたランダムな数値を含みます。ここで `fan_in` は重みテンソルの入力ユニットの数です。

# 例

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

# 参考文献

[1] Lecun, Yann, et al. "Efficient backprop." Neural networks: Tricks of the trade. Springer, Berlin, Heidelberg, 2012. 9-48.
