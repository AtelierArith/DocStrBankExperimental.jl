```
    LinearStretching <: AbstractHistogramAdjustmentAlgorithm
    LinearStretching(; [src_minval], [src_maxval],
                       dst_minval=0, dst_maxval=1,
                       no_clamp=false)

    LinearStretching((src_minval, src_maxval) => (dst_minval, dst_maxval))
    LinearStretching((src_minval, src_maxval) => nothing)
    LinearStretching(nothing => (dst_minval, dst_maxval))

    adjust_histogram([T,] img, f::LinearStretching)
    adjust_histogram!([out,] img, f::LinearStretching)
```

強度の範囲が [`dst_minval`, `dst_maxval`] の間に広がる画像を返します。

# 詳細

線形ストレッチ（*正規化*とも呼ばれる）は、画像のダイナミックレンジを変更するために使用されるコントラスト強化変換です。特に、入力画像が範囲 [A,B] のグレイ値を持ち、線形マッピングを使用してダイナミックレンジを [a,b] に変更したい場合、必要な変換は次の関係によって与えられます。

$$
f(x) = (x-A) \frac{b-a}{B-A} + a.
$$

# オプション

`adjust_histogram` および `LinearStretching` 型のパラメータに関するさまざまなオプションが以下に詳述されています。

## `img` の選択肢

この関数はさまざまな入力タイプを処理できます。返される画像は入力タイプに依存します。

カラー画像の場合、入力は [YIQ](https://en.wikipedia.org/wiki/YIQ) タイプに変換され、Y チャンネルの強度が指定された範囲にストレッチされます。修正された Y チャンネルは I および Q チャンネルと組み合わされ、結果の画像は入力と同じタイプに変換されます。

## `dst_minval` と `dst_maxval` の選択肢

宛先値範囲 `dst_minval` と `dst_maxval` が指定されている場合、強度は範囲 [`dst_minval`, `dst_maxval`] にマッピングされます。デフォルト値は 0 と 1 です。

## `src_minval` と `src_maxval` の選択肢

ソース値範囲 `src_minval` と `src_maxval` は入力画像の強度範囲を指定します。デフォルトでは、値は `extrema(img)`（有限）です。カスタム値が提供されると、出力強度値はそれを超えた場合に範囲 `[dst_minval, dst_maxval]` にクリンチされます。

## `no_clamp`

`no_clamp=true` を設定すると、出力強度値が範囲 `[dst_minval, dst_maxval]` を超えても自動クリンチが無効になります。ただし、制限された値範囲を持つタイプには依然としてクリンチが適用されます。たとえば、入力の eltype が `N0f8` の場合、`no_clamp==true` であっても出力は `[0.0N0f8, 1.0N0f8]` にクリンチされます。

# 例

```julia
using ImageContrastAdjustment, TestImages

img = testimage("mandril_gray")
# `img` のコントラストをストレッチして単位区間に広がるようにします。
imgo = adjust_histogram(img, LinearStretching(dst_minval = 0, dst_maxval = 1))
```

便利のために、`Pair` を使用して `LinearStretching` オブジェクトを構築することもサポートされています。

```julia
# これらの2つのコンストラクタは同等です
LinearStretching(src_minval=0.1, src_maxval=0.9, dst_minval=0.05, dst_maxval=0.95)
LinearStretching((0.1, 0.9) => (0.05, 0.95))

# `nothing` で置き換えてデフォルト値を使用することもできます。たとえば、
# 宛先値範囲のみを指定
LinearStretching(nothing => (0.05, 0.95))
# ソース値範囲のみを指定し、デフォルトの宛先値範囲 (0, 1) を使用
LinearStretching((0.1, 0.9) => nothing)
```

# 参考文献

1. W. Burger と M. J. Burge. *デジタル画像処理*. コンピュータサイエンスのテキスト, 2016. [doi:10.1007/978-1-4471-6684-9](https://doi.org/10.1007/978-1-4471-6684-9)

```
