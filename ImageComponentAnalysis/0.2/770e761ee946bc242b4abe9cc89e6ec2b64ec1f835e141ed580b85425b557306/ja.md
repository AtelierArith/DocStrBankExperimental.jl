```
    BoundingBox <: AbstractComponentAnalysisAlgorithm
    BoundingBox(;  box_area = true)
    analyze_components(components, f::BoundingBox)
    analyze_components!(df::AbstractDataFrame, components, f::BoundingBox)
```

ラベル付き接続成分の配列を入力として受け取り、各成分の最小（画像軸に沿った）バウンディングボックスを示す`StepRange`型のタプルを格納する列を持つ`DataFrame`を返します。

この関数はオプションでボックス面積も返すことができます。

# 例

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ColorTypes

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
measurements = analyze_components(components, BoundingBox(box_area = true))

```
