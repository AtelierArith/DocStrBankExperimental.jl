```
crossentropy(ŷ, y; dims = 1, eps = eps(eltype(ŷ)), agg = mean)
```

与えられた確率分布間のクロスエントロピーを返します。計算式は次の通りです。

```
agg(-sum(y .* log.(ŷ .+ ϵ); dims))
```

クロスエントロピーは通常、マルチクラス分類における損失として使用され、この場合、ラベル `y` はワンホット形式で与えられます。`dims` はクラス確率を含む次元（または次元）を指定します。予測 `ŷ` は `dims` にわたって1に合計されるべきであり、これは [softmax](@ref Softmax) 操作の出力と同様です。

数値的安定性のために、`softmax` の後に `crossentropy` を使用するのではなく、[`logitcrossentropy`](@ref) を使用することをお勧めします。

損失を計算する前に、[`label_smoothing`](@ref) を使用して真のラベルをスムージングします。

関連情報: [`logitcrossentropy`](@ref), [`binarycrossentropy`](@ref), [`logitbinarycrossentropy`](@ref).

# 例

```jldoctest
julia> y_label = Flux.onehotbatch([0, 1, 2, 1, 0], 0:2)
3×5 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 1  ⋅  ⋅  ⋅  1
 ⋅  1  ⋅  1  ⋅
 ⋅  ⋅  1  ⋅  ⋅

julia> y_model = softmax(reshape(-7:7, 3, 5) .* 1f0)
3×5 Matrix{Float32}:
 0.0900306  0.0900306  0.0900306  0.0900306  0.0900306
 0.244728   0.244728   0.244728   0.244728   0.244728
 0.665241   0.665241   0.665241   0.665241   0.665241

julia> sum(y_model; dims=1)
1×5 Matrix{Float32}:
 1.0  1.0  1.0  1.0  1.0

julia> Flux.crossentropy(y_model, y_label)
1.6076053f0

julia> 5 * ans ≈ Flux.crossentropy(y_model, y_label; agg=sum)
true

julia> y_smooth = Flux.label_smoothing(y_label, 0.15f0)
3×5 Matrix{Float32}:
 0.9   0.05  0.05  0.05  0.9
 0.05  0.9   0.05  0.9   0.05
 0.05  0.05  0.9   0.05  0.05

julia> Flux.crossentropy(y_model, y_smooth)
1.5776052f0
```
