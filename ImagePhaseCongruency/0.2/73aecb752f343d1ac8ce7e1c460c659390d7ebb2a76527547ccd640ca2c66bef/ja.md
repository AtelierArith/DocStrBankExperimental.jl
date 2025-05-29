画像の位相をランダム化し、振幅スペクトルは変更しません。

```
Usage:   newimg = nophase(img)

Argument:       img::AbstractArray{T,2} where T <: Real - 入力画像

Returns:     newimg::Array{Float64,2} - 位相がランダム化された画像
```

一般的に、この変換によってほとんどの画像は破壊されます。しかし、いくつかのテクスチャは「振幅のみ」の画像でかなりうまく再現されます。通常、これらは孤立したピークの数が限られた振幅スペクトルを持つテクスチャです。つまり、限られた数の強い高調波から構成されるテクスチャです。

関連情報: [`noiseonf`](@ref), [`quantizephase`](@ref), [`swapphase`](@ref)
