```
mosaicview(A::AbstractArray;
           [fillvalue=<zero unit>], [npad=0],
           [nrow], [ncol], [rowmajor=false]) -> MosaicView
mosaicview(As::AbstractArray...; kwargs...)
mosaicview(As::Union{Tuple, AbstractVector}; kwargs...)
```

配列 `A` から二次元の「ビュー」を作成します。

結果として得られる [`MosaicView`](@ref) は、`A` の最初の二次元のすべての行列スライスを単一の大きなモザイク（行列の形）として表示します。

# 引数

[`MosaicView`](@ref) のコンストラクタを直接使用するのとは対照的に、関数 `mosaicview` はいくつかの便利なキーワードを許可します。典型的な使用例は、入力画像のセットから画像モザイクを作成することです。

  * パラメータ `fillvalue` は、空白に使用される値を定義します。これは `npad` によって引き起こされるパディングや、`A` の行列スライスの数が `nrow*ncol` より少ない場合の空のモザイクタイルに該当します。
  * パラメータ `npad` は、隣接するモザイクタイル間の空のパディングスペースを定義します。これは、個々のタイル（すなわち `A` の行列スライス）が視覚的にグリッドラインで分けられるべき画像である場合に特に便利です。
  * パラメータ `nrow` と `ncol` は、モザイクが配置される行および/または列方向のタイルの数を選択するために使用できます。2つのパラメータのうち1つを指定すれば十分であり、もう1つはそれに応じて推測されます。どちらも指定されない場合のデフォルトは `nrow = size(A,3)` です。
  * `rowmajor` が `true` に設定されている場合、スライスは上から下、左から右に配置されます（デフォルトは上から下、左から右）。レイアウトは非自明な場合、すなわち `nrow != 1` および `ncol != 1` の場合にのみ異なります。

!!! tip
    この関数は型安定ではなく、パフォーマンスが優先されない場合にのみ使用するべきです。最適なパフォーマンスを達成するには、手動で [`MosaicView`](@ref) を構築する必要があります。


# 例

最も簡単な使用法は、同じ次元の2つの配列を `cat` することです。

```julia-repl
julia> A1 = fill(1, 3, 1)
3×1 Array{Int64,2}:
 1
 1
 1

julia> A2 = fill(2, 1, 3)
1×3 Array{Int64,2}:
 2  2  2

julia> mosaicview(A1, A2)
6×3 MosaicView{Int64,4, ...}:
 0  1  0
 0  1  0
 0  1  0
 0  0  0
 2  2  2
 0  0  0

julia> mosaicview(A1, A2; center=false)
 6×3 MosaicView{Int64,4, ...}:
  1  0  0
  1  0  0
  1  0  0
  2  2  2
  0  0  0
  0  0  0
```

他のキーワード引数は、見栄えの良い結果を得るために役立ちます。

```julia-repl
julia> using MosaicViews

julia> A = [k for i in 1:2, j in 1:3, k in 1:5]
2×3×5 Array{Int64,3}:
[:, :, 1] =
 1  1  1
 1  1  1

[:, :, 2] =
 2  2  2
 2  2  2

[:, :, 3] =
 3  3  3
 3  3  3

[:, :, 4] =
 4  4  4
 4  4  4

[:, :, 5] =
 5  5  5
 5  5  5

julia> mosaicview(A, ncol=2)
6×6 MosaicViews.MosaicView{Int64,4,...}:
 1  1  1  4  4  4
 1  1  1  4  4  4
 2  2  2  5  5  5
 2  2  2  5  5  5
 3  3  3  0  0  0
 3  3  3  0  0  0

julia> mosaicview(A, nrow=2)
4×9 MosaicViews.MosaicView{Int64,4,...}:
 1  1  1  3  3  3  5  5  5
 1  1  1  3  3  3  5  5  5
 2  2  2  4  4  4  0  0  0
 2  2  2  4  4  4  0  0  0

julia> mosaicview(A, nrow=2, rowmajor=true)
4×9 MosaicViews.MosaicView{Int64,4,...}:
 1  1  1  2  2  2  3  3  3
 1  1  1  2  2  2  3  3  3
 4  4  4  5  5  5  0  0  0
 4  4  4  5  5  5  0  0  0

julia> mosaicview(A, nrow=2, npad=1, rowmajor=true)
5×11 MosaicViews.MosaicView{Int64,4,...}:
 1  1  1  0  2  2  2  0  3  3  3
 1  1  1  0  2  2  2  0  3  3  3
 0  0  0  0  0  0  0  0  0  0  0
 4  4  4  0  5  5  5  0  0  0  0
 4  4  4  0  5  5  5  0  0  0  0

julia> mosaicview(A, fillvalue=-1, nrow=2, npad=1, rowmajor=true)
5×11 MosaicViews.MosaicView{Int64,4,...}:
  1   1   1  -1   2   2   2  -1   3   3   3
  1   1   1  -1   2   2   2  -1   3   3   3
 -1  -1  -1  -1  -1  -1  -1  -1  -1  -1  -1
  4   4   4  -1   5   5   5  -1  -1  -1  -1
  4   4   4  -1   5   5   5  -1  -1  -1  -1
```
