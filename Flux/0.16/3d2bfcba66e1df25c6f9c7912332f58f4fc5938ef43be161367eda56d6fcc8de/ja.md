```
LayerNorm(size..., λ=identity; affine=true, eps=1f-5)
```

再帰的隠れ状態と一緒に使用するために設計された[正規化層](https://arxiv.org/abs/1607.06450)。引数`size`は整数または整数のタプルである必要があります。

フォワードパスでは、層は入力の平均と標準偏差を正規化し、その後要素ごとの活性化`λ`を適用します。入力はタプル`size`の最初の`length(size)`次元に沿って正規化され、整数`size`の場合は最初の次元に沿って正規化されます。入力の最初の次元のサイズは`size`と等しいことが期待されます。

`affine=true`の場合、[`Scale`](@ref)層を使用して学習可能なシフトと再スケーリングも適用されます。

他に[`BatchNorm`](@ref)、[`InstanceNorm`](@ref)、[`GroupNorm`](@ref)、および[`normalise`](@ref)も参照してください。

# 例

```jldoctest
julia> using Statistics

julia> xs = rand(3, 3, 3, 2);  # 3チャネルを持つ2つの画像のバッチ

julia> m = LayerNorm(3);

julia> y = m(xs);

julia> isapprox(std(y, dims=1:3), ones(1, 1, 1, 2), atol=0.1) && std(y, dims=1:3) != std(xs, dims=1:3)
true
```
