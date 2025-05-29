```
    NonmaximaSuppression <: AbstractEdgeThinningAlgorithm
    NonmaximaSuppression(; threshold::Union{Number, Percentile} = Percentile(20))

    f = NonmaximaSuppression()
    f(out::AbstractArray, mag::AbstractArray, g₁::AbstractArray, g₂::AbstractArray, f::NonmaximaSuppression)
```

勾配の大きさ `mag` の局所的な最大値を局所的な勾配方向に沿って孤立させ、その結果を `out` に格納します。引数 `g₁` と `g₂` は、それぞれ第一空間次元（y）および第二空間次元（x）における勾配を表します。

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
# NonmaximaSuppressionファンクタをインスタンス化します。
f = NonmaximaSuppression()

# 非最大勾配の大きさを抑制し、結果を `nms` に格納します。
f(nms, mag, g₁, g₂)

imshow(img)
imshow(mag)
imshow(nms)
```

# 参考文献

J. Canny, "A Computational Approach to Edge Detection," in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. PAMI-8, no. 6, pp. 679-698, Nov. 1986, doi: 10.1109/TPAMI.1986.4767851.
