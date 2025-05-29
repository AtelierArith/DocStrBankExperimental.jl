```
entropy(logᵦ, img; nbins=256)
entropy(img; kind=:shannon, nbins=256)
```

画像信号のエントロピーを `-sum(p.*logᵦ(p))` として計算します。ここで、p は画像のヒストグラムです。

対数の底 β（エントロピー単位とも呼ばれる）は次のいずれかです：

  * `:shannon`（底 2 の対数、デフォルト）、または logᵦ = log2 を使用
  * `:nat`（底 e の対数）、または logᵦ = log を使用
  * `:hartley`（底 10 の対数）、または logᵦ = log10 を使用

キーワード `nbins` はヒストグラムの計算方法を制御します。

# 例

```jldoctest; setup=:(using ImageQualityIndexes, Random; Random.seed!(0))
julia> img = rand(1:10, 5, 5)
5×5 Matrix{Int64}:
 2  8   2  5  6
 7  9   2  7  3
 7  8   8  1  3
 3  1   3  9  4
 5  7  10  4  6

julia> entropy(img)
3.223465189601647

julia> entropy(log2, img) # kind=:shannon
3.223465189601647

julia> entropy(img; kind=:nat)
2.234335807805511
```

分布（ヒストグラム）が同じであれば、エントロピーも同じになります：

```jldoctest; setup=:(using ImageQualityIndexes, ImageCore, Random; Random.seed!(0))
julia> img = rand(Gray, 5, 5);

julia> entropy(img)
4.5638561897747225

julia> entropy(RGB.(img))
4.5638561897747225

julia> entropy(repeat(img, inner=(2, 2), outer=(2, 2)))
4.5638561897747225
```
