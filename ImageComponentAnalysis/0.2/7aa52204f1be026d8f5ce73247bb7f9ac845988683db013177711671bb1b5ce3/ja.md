```
    BasicTopology <: AbstractComponentAnalysisAlgorithm
    BasicTopology(; holes = true,  euler_number = true)
    analyze_components(components, f::BasicTopolgy)
    analyze_components!(dataframe::AbstractDataFrame, components, f::BasicTopolgy)
```

ラベル付きの連結成分の配列を入力として受け取り、各成分の基本的なトポロジー特性（`euler_number`や`holes`の総数など）を格納する列を持つ`DataFrame`を返します。

この関数は、`4-connected`と`8-connected`の隣接関係に対応する`euler_number`の2つのバリアントを返します：`euler₄`と`euler₈`。

`euler_number`と`holes`の数は、[1]で説明されている特定の2 × 2ピクセルパターンである*bit-quad*パターンから導出されます。したがって、この関数は、列名`Q₀, Q₁, Q₂, Q₃, Q₄`および`Qₓ`の下に6つのbit-quadパターンを`DataFrame`に追加します。

# 例

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ColorTypes

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
measurements = analyze_components(components, BasicTopology(holes = true, euler_number = true))

```

# 参考文献

1. S. B. Gray, “Local Properties of Binary Images in Two Dimensions,” IEEE Transactions on Computers, vol. C–20, no. 5, pp. 551–561, May 1971.
