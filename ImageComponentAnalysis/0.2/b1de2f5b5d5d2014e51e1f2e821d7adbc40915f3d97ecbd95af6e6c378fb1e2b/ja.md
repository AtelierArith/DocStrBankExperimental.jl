```
    establish_contour_hierarchy(labels::AbstractArray{<:Integer})
```

ラベル付けされた各コンポーネントの外部境界と穴の境界の輪郭をトレースし、輪郭間の階層関係をツリー構造に格納します。

# 詳細

ツリーは[`LeftChildRightSiblingTree`](https://github.com/JuliaCollections/LeftChildRightSiblingTrees.jl)型であり、[`AbstractTrees.jl`](https://github.com/JuliaCollections/AbstractTrees.jl)パッケージの機能を使用して反復処理できます。

ツリーの各`Node`は、[`DigitalContour`](@ref)型の`data`フィールドを持っています。

ツリーの親/子関係は、接続されたコンポーネントのネスティングを反映しています。接続されたコンポーネントが別の接続されたコンポーネントの内部に完全に含まれている場合、その輪郭は周囲の接続されたコンポーネントの輪郭の子になります。

# 例

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ImageCore, AbstractTrees, Parameters

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
tree = establish_contour_hierarchy(components)

# ツリー内のすべてのDigitalContourを反復処理します。
for node in PostOrderDFS(tree)
    @unpack id, is_outer, pixels node.data # Parameters.jlの"@unpack"を参照
    @show id, is_outer, pixels
end
```

# 参考文献

1. S. Suzuki and K. Abe, “Topological structural analysis of digitized binary images by border following,” Computer Vision, Graphics, and Image Processing, vol. 29, no. 3, p. 396, Mar. 1985.
