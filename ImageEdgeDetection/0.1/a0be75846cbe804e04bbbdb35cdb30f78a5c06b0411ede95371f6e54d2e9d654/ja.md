```
    SubpixelNonmaximaSuppression <: AbstractEdgeThinningAlgorithm
    SubpixelNonmaximaSuppression(; threshold::Union{Number, Percentile} = Percentile(20))

    f = SubpixelNonmaximaSuppression()
    f(out₁::AbstractArray, out₂::Matrix{<:AbstractArray}, mag::AbstractArray, g₁::AbstractArray, g₂::AbstractArray, f::SubpixelNonmaximaSuppression)
```

勾配の大きさ `mag` の局所的な最大値を局所的な勾配方向に沿ってサブピクセル精度で孤立させます。引数 `g₁` と `g₂` はそれぞれ第一空間次元（y）および第二空間次元（x）における勾配を表します。

局所的な最大値の整数成分は、非ゼロの行および列のエントリ `out₁` に対応します。付随するサブピクセルオフセットは、長さ2のベクトルとして2次元配列 `out₂` に格納されます。サブピクセルオフセットを整数成分に加えることで、サブピクセル座標を復元できます。

# 詳細

TODO

# 例

```julia

using TestImages, FileIO, ImageView, ImageEdgeDetection, ImageFiltering

img =  testimage("mandril_gray")

# 第一および第二空間次元における勾配
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# 勾配の大きさ
mag = hypot.(g₁, g₂)

nms = zeros(eltype(mag), axes(mag))
subpixel_offsets = zeros(SVector{2,Float64}, axes(mag))

# NonmaximaSuppressionファンクタをインスタンス化します。
f = SubpixelNonmaximaSuppression()

# 非最大勾配の大きさを抑制し、結果を `nms` に格納します。
f(nms, subpixel_offsets, mag, g₁, g₂)

imshow(img)
imshow(mag)
imshow(nms)
```

# 参考文献

1. J. Canny, "A Computational Approach to Edge Detection," in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. PAMI-8, no. 6, pp. 679-698, Nov. 1986, doi: 10.1109/TPAMI.1986.4767851.
2. F. Devernay, "A non-maxima suppression method for edge detection with sub-pixel accuracy", Tech. Report RR-2724, INRIA, 1995.
