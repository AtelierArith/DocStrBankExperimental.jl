```
Polysegment <: AbstractImageBinarizationAlgorithm
Polysegment()

binarize([T,] img, f::Polysegment)
binarize!([out,] img, f::Polysegment)
```

*多項式セグメンテーション*技術を使用して、画像のピクセルを2つのカテゴリ（前景と背景）にグループ化します。

# 出力

バイナライズされた画像を`Array{Gray{T}}`として返します。サイズは`size(img)`です。`T`が指定されていない場合、`out`と`img`から推測されます。

# 拡張ヘルプ

# 詳細

このアプローチは、2つのクラスタ中心（すなわち前景と背景）の灰色レベルを表す多項式の2つの根を持つ一変数の2次多項式を構築することを含みます。ピクセルは、どのクラスタ中心が最も近いかに応じて前景または背景に割り当てられます。

# 引数

関数の引数は以下でより詳細に説明されています。

## `img::AbstractArray`

バイナライズする必要がある画像。画像は自動的に`Gray`に変換されます。

# 例

`TestImages`パッケージの「カメラマン」画像をバイナライズします。

```julia
using TestImages, ImageBinarization

img = testimage("cameraman")
img_binary = binarize(img, Polysegment())
```

## 参考文献

1. R. E. Vidal, "Generalized Principal Component Analysis (GPCA): An Algebraic Geometric Approach to Subspace Clustering and Motion Segmentation." Order No. 3121739, University of California, Berkeley, Ann Arbor, 2003.
