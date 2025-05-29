```
    Contour <: AbstractComponentAnalysisAlgorithm
    Contour()
    analyze_components(components, f::Contour)
    analyze_components!(df::AbstractDataFrame, components, f::Contour)
```

ラベル付きの連結成分の配列を入力として受け取り、各連結成分の輪郭を格納する列を持つ `DataFrame` を返します。

輪郭のトポロジー（階層）に関する情報が必要な場合は、`establish_contour_hierarchy` 関数を使用して、輪郭のネストを反映し、すべての輪郭ピクセルを [`DigitalContour`](@ref) 型に格納するツリー構造を取得できます。

# 例

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ImageCore, AbstractTrees

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
measurements = analyze_components(components, Contour())

```

# 参考文献

1. S. Suzuki and K. Abe, “Topological structural analysis of digitized binary images by border following,” Computer Vision, Graphics, and Image Processing, vol. 29, no. 3, p. 396, Mar. 1985.
