```
AlphaDropout(p; [rng, active])
```

ドロップアウト層です。[自己正規化ニューラルネットワーク](https://arxiv.org/abs/1706.02515)で使用されます。AlphaDropout層は、活性化の平均と分散が以前と同じであることを保証します。

[`testmode!`](@ref) が true の場合、入力には何も行いません。

# 例

```jldoctest
julia> using Statistics

julia> x = randn32(1000,1);

julia> m = Chain(Dense(1000 => 1000, selu), AlphaDropout(0.2));

julia> Flux.trainmode!(m);

julia> y = m(x);

julia> isapprox(std(x), std(y), atol=0.2)
true
```
