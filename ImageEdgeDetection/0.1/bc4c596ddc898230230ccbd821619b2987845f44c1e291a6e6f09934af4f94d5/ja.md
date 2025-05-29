```
    Canny <: AbstractEdgeDetectionAlgorithm
    Canny(; spatial_scale = 1, high = Percentile(80), low = Percentile(20), thinning_algorithm = NonmaximaSuppression(threshold = low))

    detect_edges([T,] img, f::Canny)
    detect_edges!([out,] img, f::Canny)
    detect_subpixel_edges([T₁, T₂] img, f::Canny)
    detect_subpixel_edges!(out₁, out₂, img, f::Canny)
```

入力画像のエッジを示すバイナリ画像を返します。

# 詳細

TODO

# オプション

`detect_edges`関数および`Canny`型のパラメータに関するさまざまなオプションが以下に詳述されています。

# imgの選択肢

`detect_edges`関数はさまざまな入力タイプを処理できます。デフォルトでは、返される画像の型は入力画像の型と一致します。

カラー画像の場合、入力はグレースケールに変換されます。

# `Canny`における`spatial_scale`の選択肢。

`spatial_scale`はガウシアンフィルタの半径(σ)を決定します。正の実数でなければなりません。

# `Canny`における`high`および`low`の選択肢。

ヒステリシス閾値`high`および`low`(`high` > `low`)は、正の数または`Percentiles`として指定できます。指定しない場合、デフォルト値`high = Percentile(80)`および`low = Percentile(20)`が仮定されます。

# `Canny`における`thinning_algorithm`の選択肢。

[`AbstractEdgeThinningAlgorithm`](@ref)を指定できます。デフォルトでは、非最大抑制をピクセルレベルの精度まで抑制する[`NonmaximaSuppression`](@ref)アルゴリズムが使用されます。サブピクセル精度を指定するには、[`SubpixelNonmaximaSuppression`](@ref)アルゴリズムを指定します。

# 例

```julia

using TestImages, FileIO, ImageView

img =  testimage("mandril_gray")
img_edges = detect_edges(img, Canny(spatial_scale = 1.4))

imshow(img)
imshow(img_edges)
```

# 参考文献

J. Canny, "A Computational Approach to Edge Detection," in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. PAMI-8, no. 6, pp. 679-698, Nov. 1986, doi: 10.1109/TPAMI.1986.4767851.
