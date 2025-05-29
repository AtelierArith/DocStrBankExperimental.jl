```
    MinimumOrientedBoundingBox <: AbstractComponentAnalysisAlgorithm
    MinimumOrientedBoundingBox(;  oriented_box_area = true, oriented_box_aspect_ratio = true)
    analyze_components(components, f::MinimumOrientedBoundingBox)
    analyze_components!(df::AbstractDataFrame, components, f::MinimumOrientedBoundingBox)
```

ラベル付き接続成分の配列を入力として受け取り、各成分の最小指向境界ボックスの4つのコーナーポイントを含む長さ4のベクトルを格納する列を持つ`DataFrame`を返します。オプションで、最小指向境界ボックスの面積とアスペクト比も返します。

# 例

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ColorTypes

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
algorithm = MinimumOrientedBoundingBox(oriented_box_area = true, oriented_box_aspect_ratio = true)
measurements = analyze_components(components, algorithm)

```
