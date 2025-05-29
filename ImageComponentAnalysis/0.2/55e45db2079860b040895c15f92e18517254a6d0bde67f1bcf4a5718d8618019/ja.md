```
    BasicMeasurement <: AbstractComponentAnalysisAlgorithm
    BasicMeasurement(; area = true,  perimeter = true)
    analyze_components(components, f::BasicMeasurement)
    analyze_components!(dataframe::AbstractDataFrame, components, f::BasicMeasurement)
```

ラベル付き接続成分の配列を入力として受け取り、各成分の基本的な測定値（`area`や`perimeter`など）を格納する列を持つ`DataFrame`を返します。

# 詳細

`area`および`perimeter`の測定値は、[1]で説明されている特定の2 × 2ピクセルパターンである*bit-quad*パターンから導出されます。したがって、関数は`DataFrame`に列名`Q₀, Q₁, Q₂, Q₃, Q₄`および`Qₓ`の下に6つのbit-quadパターンを追加します。

関数は`perimeter`の2つの測定値、*perimiter₀*および*perimter₁*を返します。これらは[2]の式18.2-8bおよび18.2-7aによって与えられます。

# 例

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ColorTypes

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
measurements = analyze_components(components, BasicMeasurement(area = true, perimeter = false))

```

# 参考文献

1. S. B. Gray, “Local Properties of Binary Images in Two Dimensions,” IEEE Transactions on Computers, vol. C–20, no. 5, pp. 551–561, May 1971.
2. Pratt, William K., Digital Image Processing, New York, John Wiley & Sons, Inc., 1991, p. 629.
