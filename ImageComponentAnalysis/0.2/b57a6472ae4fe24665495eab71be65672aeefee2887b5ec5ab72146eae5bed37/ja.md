```
    EllipseRegion <: AbstractComponentAnalysisAlgorithm
    EllipseRegion(;  centroid = true, semiaxes = true, orientation = true, eccentricity = true)
    analyze_components(components, f::EllipseRegion)
    analyze_components!(df::AbstractDataFrame, components, f::EllipseRegion)
```

ラベル付きの連結成分の配列を入力として受け取り、各成分の最適フィット楕円領域のパラメータを格納する列を持つ `DataFrame` を返します。楕円のパラメータは次のとおりです。

1. `centroid`: 楕円の中心を表す長さ2の `SVector`。
2. `semiaxes`: セミメジャー軸とセミマイナー軸の長さをそれぞれ表す長さ2の `SVector`。
3. `orientation` ∈ [-90, 90): 正のx軸に対するセミメジャー軸の向きを度で表したもの。
4. `eccentricity`: 楕円がどれだけ円に近いかを示す指標。

楕円領域は [画像モーメント](https://en.wikipedia.org/wiki/Image_moment) から推定されるため、関数は `DataFrame` に `M₀₀, M₁₀, M₀₁, M₁₁, M₂₀` および `M₀₂` という列名の下にモーメントを追加します。

# 例

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ImageCore, AbstractTrees

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
measurements = analyze_components(components, EllipseRegion())

```

# 参考文献

1. [1] M. R. Teague, “Image analysis via the general theory of moments*,” Journal of the Optical Society of America, vol. 70, no. 8, p. 920, Aug. 1980.
