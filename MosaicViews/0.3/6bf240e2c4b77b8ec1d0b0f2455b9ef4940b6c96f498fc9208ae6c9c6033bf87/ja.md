```
MosaicView(A::AbstractArray)
```

三次元または四次元配列 `A` の二次元「ビュー」を作成します。結果として得られる `MosaicView` は、`A` の第三次元のすべての要素に対して `vcat` を使用し、第四次元のすべての要素に対して `hcat` を使用するように `A` のデータを表示します。

例えば、`size(A)` が `(2,3,4)` の場合、結果として得られる `MosaicView` のサイズは `(2*4,3)` であり、これは `(8,3)` になります。あるいは、`size(A)` が `(2,3,4,5)` の場合、結果のサイズは `(2*4,3*5)` であり、これは `(8,15)` になります。

別の考え方をすると、`MosaicView` は与えられた3Dまたは4D配列 `A` の第三（およびオプションで第四）次元に列挙されたすべての個々の行列のモザイクを作成します。これは、同じサイズの画像のセットから単一の合成画像を作成するのに特に便利です。

```@jldoctest
julia> using MosaicViews

julia> A = [(k+1)*l-1 for i in 1:2, j in 1:3, k in 1:2, l in 1:2]
2×3×2×2 Array{Int64,4}:
[:, :, 1, 1] =
 1  1  1
 1  1  1

[:, :, 2, 1] =
 2  2  2
 2  2  2

[:, :, 1, 2] =
 3  3  3
 3  3  3

[:, :, 2, 2] =
 5  5  5
 5  5  5

julia> MosaicView(A)
4×6 MosaicViews.MosaicView{Int64,4,Array{Int64,4}}:
 1  1  1  3  3  3
 1  1  1  3  3  3
 2  2  2  5  5  5
 2  2  2  5  5  5
```
