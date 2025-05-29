```julia
struct IntensityMap{T, N, D, G<:(ComradeBase.AbstractRectiGrid{D}), A<:AbstractArray{T, N}, R<:Tuple, Na} <: DimensionalData.AbstractDimArray{T, N, D, A<:AbstractArray{T, N}}
```

この型は、`ComradeBase` インターフェースに従うすべての画像とモデルの基本的な配列型です。この型は `DimensionalData.AbstractDimArray` のサブタイプですが、Comrade API をサポートするためにいくつかの変更を加えています。

1. 次元は `AbstractRectiGrid` インターフェースによって指定されるべきです。通常、ユーザーは直交グリッドのために [`RectiGrid`](@ref) グリッドだけを必要とします。
2. 配列の次元にアクセスする方法は2つあります。`dims(img)` は通常の `DimArray` 次元、すなわち `Tuple{DimensionalData.Dim, ...}` を返します。配列の次元にアクセスするもう一つの方法は `getproperty` を使用することで、例えば `img.X` は通常の `DimensionalData.Dimension` の素材を取り除いた RA/X グリッドの位置を返します。この `getproperty` の動作は *安定した API の一部とは見なされず*、将来的に変更される可能性があります。
3. メタデータは `AbstractRectiGrid` 型の `header` プロパティに保存され、`metadata` または `header` を通じてアクセスできます。

`IntensityMap` を作成する最も一般的な方法は、関数定義を使用することです。

```julia-repl
julia> g = imagepixels(10.0, 10.0, 128, 128; header=NoHeader())
julia> X = g.X; Y = g.Y
julia> data = rand(128, 128)
julia> img1 = IntensityMap(data, g)
julia> img2 = IntensityMap(data, (;X, Y); header=header(g))
julia> img1 == img2
true
julia> img3 = IntensityMap(data, 10.0, 10.0; header=NoHeader())
```

ブロードキャスティング、マップ、および削減はすべて `DimensionalData` インターフェースに従うべきです。
