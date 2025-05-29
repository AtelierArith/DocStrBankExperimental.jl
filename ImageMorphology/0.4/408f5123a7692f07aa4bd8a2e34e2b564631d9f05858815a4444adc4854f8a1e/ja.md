```
hminima(img, h; [dims])
hminima(img, h; se)
```

深さ h の領域最小値を計算します。

グレースケール画像 `img` に対して、hminima 変換は、深さが指定された閾値レベル `h` 未満のすべての領域最小値を抑制します。

`dims` キーワードは、ボックス形状の構造要素 [`strel_box(img; dims)`](@ref strel_box) を構築することによって処理する次元を指定するために使用されます。一般的な構造要素の場合、半サイズは各次元に沿って `0` または `1` であることが期待されます。

# 例

```jldoctest; setup=:(using ImageMorphology, ImageMorphology.FixedPointNumbers) julia> img = UInt8[8 8 8 8 8 8 8 8 8 8; 8 7 7 7 8 8 7 7 7 8; 8 7 6 7 8 8 7 3 7 8; 8 7 7 7 8 8 7 7 7 8; 8 8 8 8 8 8 8 8 8 8] 5×10 Matrix{UInt8}:  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x07  0x06  0x07  0x08  0x08  0x07  0x03  0x07  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08

julia> out = hminima(reinterpret(N0f8, img), reinterpret(N0f8, UInt8(3))) 5×10 Array{N0f8,2} with eltype N0f8:  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.027  0.027  0.027  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.027  0.024  0.027  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.027  0.027  0.027  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031

julia> ref_img = UInt8[8 8 8 8 8 8 8 8 8 8; 8 8 8 8 8 8 7 7 7 8; 8 8 8 8 8 8 7 6 7 8; 8 8 8 8 8 8 7 7 7 8; 8 8 8 8 8 8 8 8 8 8] 5×10 Matrix{UInt8}:  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x07  0x06  0x07  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08

julia> eltype(out) == N0f8 true

julia> out == reinterpret(N0f8, ref_img) true

# 参照

この関数のインプレースバージョンは `hminima!` です。

# 参考文献

  * [1] L. Vincent, “Morphological grayscale reconstruction in image analysis: applications and efficient algorithms,” IEEE Trans. on Image Process., vol. 2, no. 2, pp. 176–201, Apr. 1993, doi: 10.1109/83.217222.
  * [2] P. Soille, Morphological Image Analysis. Berlin, Heidelberg: Springer Berlin Heidelberg, 2004. doi: 10.1007/978-3-662-05088-0.
```
