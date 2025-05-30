```
SingleHistogramThreshold <: AbstractImageBinarizationAlgorithm
SingleHistogramThreshold(alg::AbstractThresholdAlgorithm; nbins=256)

binarize([T,] img, f::AbstractThresholdAlgorithm; nbins=256)
binarize!([out,] img, f::AbstractThresholdAlgorithm; nbins=256)
```

画像 `img` を、指定された閾値探索アルゴリズム `alg` によって見つかった閾値を使用して二値化します。

# 出力

二値化された画像を `Array{Gray{T}}` として返します。サイズは `size(img)` です。`T` が指定されていない場合、`out` と `img` から推測されます。

# 引数

関数の引数については、以下で詳しく説明します。

## `img::AbstractArray`

二値化する必要がある画像です。画像は自動的に `Gray` に変換され、必要なグレーレベルのヒストグラムが構築されます。

## `alg::AbstractThresholdAlgorithm`

`AbstractThresholdAlgorithm` は `HistogramThreshold.jl` パッケージの `ThresholdAPI.jl` で定義された抽象型で、さまざまな閾値探索アルゴリズムを提供します：

  * `HistogramThresholding.Balanced`
  * `HistogramThresholding.Entropy`
  * `HistogramThresholding.Intermodes`
  * `HistogramThresholding.MinimumError`
  * `HistogramThresholding.MinimumIntermodes`
  * `HistogramThresholding.Moments`
  * `HistogramThresholding.Otsu`
  * `HistogramThresholding.UnimodalRosin`
  * `HistogramThresholding.Yen`

詳細な説明や構築については、各具体的なアルゴリズムを参照してください。たとえば、REPLで `?Otsu` と入力すると、`Otsu` メソッドの使用方法についての詳細が得られます。

## `nbins::Integer`

ヒストグラムを構築するために使用される離散ビンの数です。小さい `nbins` は、ノイズが少なく、言い換えれば、より滑らかな出力を提供する可能性があります。デフォルト値は `256` です。

# 例

すべての使用法は同じパターンに従い、`Otsu` を例に取ります：

```julia
using TestImages, ImageBinarization

img = testimage("cameraman")
img_binary = binarize(img, Otsu())
```

便利さは劣りますが、`SingleHistogramThreshold` を自分で構築することもできます：

```julia
using TestImages, ImageBinarization

img = testimage("cameraman")
f = SingleHistogramThreshold(Otsu(), nbins=256)
img_binary = binarize(img, f)
```
