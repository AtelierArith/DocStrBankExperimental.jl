```
DimArray <: AbstractDimArray

DimArray(data, dims, refdims, name, metadata)
DimArray(data, dims::Tuple; refdims=(), name=NoName(), metadata=NoMetadata())
```

[`AbstractDimArray`](@ref) の主な具体的サブタイプです。

`DimArray` は、変換を通じてその `Dimension` を維持および更新し、次元を参照次元 `refdims` に移動します（例えば、`mean` のような削減操作の後に）。

## 引数

  * `data`: `AbstractArray`。
  * `dims`: `Dimension` の `Tuple`。
  * `name`: 配列の文字列名。プロットやテーブルに表示されます。
  * `refdims`: 参照次元。通常、プログラム的に設定され、ラベリングや再構築のために過去のスライスや次元の削減を追跡します。
  * `metadata`: `Dict` または `Metadata` オブジェクト、または `NoMetadata()`。

インデックス付けは、すべての通常のインデックス、または [`Dimension`](@ref) および/または [`Selector`](@ref) を使用して行うことができます。

非範囲の `AbstractArray` で `AbstractDimArray` にインデックスを付けることは、`Dimension` インデックスに未定義の影響を与えます。順序付き配列のみを使用してください。

例:

```julia
using Dates, DimensionalData

ti = (Ti(DateTime(2001):Month(1):DateTime(2001,12)),
x = X(10:10:100))
A = DimArray(rand(12,10), (ti, x), "example")

julia> A[X(Near([12, 35])), Ti(At(DateTime(2001,5)))];

julia> A[Near(DateTime(2001, 5, 4)), Between(20, 50)];
```
