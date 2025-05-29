画像間の位相 - 振幅スワッピングを示します。

```
Usage:   (newimg1, newimg2) = swapphase(img1, img2)

Arguments:
 img1, img2::Array{<:Real,2} - 同じサイズの2つの画像を入力として使用

Returns:
    newimg1::Array{Float64,2} - img1の位相とimg2の振幅から得られた画像。
    newimg2::Array{Float64,2} - img2の位相、img1の振幅。
```

参照: [`quantizephase`](@ref), [`nophase`](@ref)
