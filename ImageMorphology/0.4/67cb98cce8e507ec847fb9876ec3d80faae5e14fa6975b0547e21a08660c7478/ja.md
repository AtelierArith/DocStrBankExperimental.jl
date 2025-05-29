```
hmaxima(img, h; [dims])
hmaxima(img, h; se)
```

高さ h の領域最大値を計算します。

グレースケール画像 `img` に対して、hmaxima 変換は、指定された閾値レベル `h` よりも低い高さのすべての領域最大値を抑制します。

`dims` キーワードは、ボックス形状の構造要素 [`strel_box(img; dims)`](@ref strel_box) を構築することによって処理する次元を指定するために使用されます。一般的な構造要素の場合、半サイズは各次元に沿って `0` または `1` であることが期待されます。

# 例

```jldoctest; setup=:(using ImageMorphology, ImageMorphology.FixedPointNumbers)
julia> img = UInt8[3 3 3 3 3 3 3 3 3 3; 3 4 4 4 3 3 4 4 4 3; 3 4 5 4 3 3 4 9 4 3; 3 4 4 4 3 3 4 4 4 3; 3 3 3 3 3 3 3 3 3 3]
5×10 Matrix{UInt8}:
 0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03
 0x03  0x04  0x04  0x04  0x03  0x03  0x04  0x04  0x04  0x03
 0x03  0x04  0x05  0x04  0x03  0x03  0x04  0x09  0x04  0x03
 0x03  0x04  0x04  0x04  0x03  0x03  0x04  0x04  0x04  0x03
 0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03

julia> out = hmaxima(reinterpret(N0f8, img), reinterpret(N0f8, UInt8(3)))
5×10 Array{N0f8,2} with eltype N0f8:
 0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012
 0.012  0.012  0.012  0.012  0.012  0.012  0.016  0.016  0.016  0.012
 0.012  0.012  0.012  0.012  0.012  0.012  0.016  0.024  0.016  0.012
 0.012  0.012  0.012  0.012  0.012  0.012  0.016  0.016  0.016  0.012
 0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012

julia> ref_img = UInt8[3 3 3 3 3 3 3 3 3 3; 3 3 3 3 3 3 4 4 4 3; 3 3 3 3 3 3 4 6 4 3; 3 3 3 3 3 3 4 4 4 3; 3 3 3 3 3 3 3 3 3 3]
5×10 Matrix{UInt8}:
 0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03
 0x03  0x03  0x03  0x03  0x03  0x03  0x04  0x04  0x04  0x03
 0x03  0x03  0x03  0x03  0x03  0x03  0x04  0x06  0x04  0x03
 0x03  0x03  0x03  0x03  0x03  0x03  0x04  0x04  0x04  0x03
 0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03

julia> eltype(out) == N0f8
true

julia> out == reinterpret(N0f8, ref_img)
true
```

# 参照

この関数のインプレースバージョンは `hmaxima!` です。

# 参考文献

  * [1] L. Vincent, “Morphological grayscale reconstruction in image analysis: applications and efficient algorithms,” IEEE Trans. on Image Process., vol. 2, no. 2, pp. 176–201, Apr. 1993, doi: 10.1109/83.217222.
  * [2] P. Soille, Morphological Image Analysis. Berlin, Heidelberg: Springer Berlin Heidelberg, 2004. doi: 10.1007/978-3-662-05088-0.

```
