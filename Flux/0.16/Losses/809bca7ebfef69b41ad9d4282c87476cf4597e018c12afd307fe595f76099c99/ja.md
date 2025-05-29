```
binarycrossentropy(ŷ, y; agg = mean, eps = eps(eltype(ŷ)))
```

バイナリクロスエントロピー損失を返します。計算は次のように行います。

```
agg(@.(-y * log(ŷ + ϵ) - (1 - y) * log(1 - ŷ + ϵ)))
```

通常、予測 `ŷ` は [sigmoid](@ref man-activations) 活性化の出力によって与えられます。`ϵ == eps` の項は無限大を避けるために含まれています。数値的安定性のために `binarycrossentropy` よりも [`logitbinarycrossentropy`](@ref) の使用が推奨されます。

損失を計算する前に、前処理として [`label_smoothing`](@ref) を使用して `y` 値をスムージングします。

関連情報: [`crossentropy`](@ref), [`logitcrossentropy`](@ref)。

# 例

```jldoctest
julia> y_bin = Bool[1,0,1]
3-element Vector{Bool}:
 1
 0
 1

julia> y_prob = softmax(reshape(vcat(1:3, 3:5), 2, 3) .* 1f0)
2×3 Matrix{Float32}:
 0.268941  0.5  0.268941
 0.731059  0.5  0.731059

julia> Flux.binarycrossentropy(y_prob[2,:], y_bin)
0.43989f0

julia> all(p -> 0 < p < 1, y_prob[2,:])  # else DomainError
true

julia> y_hot = Flux.onehotbatch(y_bin, 0:1)
2×3 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 ⋅  1  ⋅
 1  ⋅  1

julia> Flux.crossentropy(y_prob, y_hot)
0.43989f0
```
