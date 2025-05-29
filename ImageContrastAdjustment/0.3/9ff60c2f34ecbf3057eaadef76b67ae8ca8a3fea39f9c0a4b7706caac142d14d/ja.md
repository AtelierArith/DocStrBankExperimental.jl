```
    ContrastStretching <: AbstractHistogramAdjustmentAlgorithm
    ContrastStretching(; t = 0.5,  slope = 1.0)

    adjust_histogram([T,] img, f::ContrastStretching)
    adjust_histogram!([out,] img, f::ContrastStretching)
```

`t` 未満の強度は狭い範囲の暗い強度に圧縮され、`t` を超える値は狭い範囲の明るい強度に圧縮された画像を返します。

# 詳細

コントラストストレッチングは、飽和近くのコントラストを強化または減少させる変換です（`slope` > 1 または < 1 の場合、それぞれ）。これは次の関係式で表されます。

$$
f(x) = \frac{1}{1 + \left(\frac{t}{x} \right)^s}, \; s \in \mathbb{R},
$$

ここで、$s$ は `slope` 引数を表します。

# オプション

`adjust_histogram` および `ContrastStretching` 型のパラメータに関するさまざまなオプションが以下に詳述されています。

## `img` の選択肢

この関数はさまざまな入力タイプを処理できます。返される画像は入力タイプに依存します。

カラー画像の場合、入力は [YIQ](https://en.wikipedia.org/wiki/YIQ) タイプに変換され、Y チャンネルの強度が指定された範囲にストレッチされます。修正された Y チャンネルは I および Q チャンネルと組み合わされ、結果の画像は入力と同じタイプに変換されます。

## `t` の選択肢

`t` の値は単位区間内である必要があります。指定しない場合はデフォルト値の 0.5 が使用されます。

## `slope` の選択肢

`slope` の値は任意の実数にすることができます。指定しない場合はデフォルト値の 1.0 が使用されます。

# 例

```julia
using ImageContrastAdjustment, ImageView, TestImages

img = testimage("mandril_gray")
ret = adjust_histogram(img, ContrastStretching(t = 0.6, slope = 3))

```

# 参考文献

1. Gonzalez, R. C., Woods, R. E., & Eddins, S. L. (2004). *Digital image processing using MATLAB* (Vol. 624). Upper Saddle River, New Jersey: Pearson-Prentice-Hall.
