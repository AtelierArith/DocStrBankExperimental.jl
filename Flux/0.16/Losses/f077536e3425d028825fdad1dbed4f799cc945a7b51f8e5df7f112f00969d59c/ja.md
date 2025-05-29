```
label_smoothing(y::Union{Number, AbstractArray}, α; dims::Int=1)
```

スムーズなラベルを返します。これは、ラベル値に対する信頼度が緩和されることを意味します。

`y` がワンホットベクトルまたはワンホットのバッチとして与えられた場合、次のように計算されます。

```
y .* (1 - α) .+ α / size(y, dims)
```

`y` がバイナリ分類のための数値または数値のバッチとして与えられた場合、次のように計算されます。

```
y .* (1 - α) .+ α / 2
```

この場合、ラベルは `0.5` に向かって圧縮されます。

α は (0, 1) の区間にある数値で、スムージングファクターと呼ばれます。α の値が大きいほど、`y` のスムージングが大きくなります。

`dims` はワンホット次元を示しますが、`dims=0` の場合は、単一の数値でエンコードされたバイナリ分布にラベルスムージングを適用することを示します。

# 例

```jldoctest
julia> y = Flux.onehotbatch([1, 1, 1, 0, 1, 0], 0:1)
2×6 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 ⋅  ⋅  ⋅  1  ⋅  1
 1  1  1  ⋅  1  ⋅

julia> y_smoothed = Flux.label_smoothing(y, 0.2f0)
2×6 Matrix{Float32}:
 0.1  0.1  0.1  0.9  0.1  0.9
 0.9  0.9  0.9  0.1  0.9  0.1

julia> y_sim = softmax(y .* log(2f0))
2×6 Matrix{Float32}:
 0.333333  0.333333  0.333333  0.666667  0.333333  0.666667
 0.666667  0.666667  0.666667  0.333333  0.666667  0.333333

julia> y_dis = vcat(y_sim[2,:]', y_sim[1,:]')
2×6 Matrix{Float32}:
 0.666667  0.666667  0.666667  0.333333  0.666667  0.333333
 0.333333  0.333333  0.333333  0.666667  0.333333  0.666667

julia> Flux.crossentropy(y_sim, y) < Flux.crossentropy(y_sim, y_smoothed)
true

julia> Flux.crossentropy(y_dis, y) > Flux.crossentropy(y_dis, y_smoothed)
true
```
