```
imresize(img, sz) -> imgr
imresize(img, inds) -> imgr
imresize(img; ratio) -> imgr
```

`img`をサイズ`sz`に変更します（またはインデックス`inds`を持つようにします）。`ratio`が使用される場合、`sz = ceil(Int, size(img).*ratio)`となります。これはサブピクセル位置での値を補間します。画像を縮小する場合、最初に`img`をローパスフィルタリングしないとエイリアシングのリスクがあります。

キーワード`method`は、Interpolations.jlからの任意のInterpolationTypeまたはDegreeを受け取り、その度数のBSpline補間を定義するために使用され、画像のリサイズに使用される補間方法を設定します。

# 例

```julia
julia> img = testimage("lena_gray_256") # 256*256
julia> imresize(img, 128, 128) # 128*128
julia> imresize(img, 1:128, 1:128) # 128*128
julia> imresize(img, (128, 128)) # 128*128
julia> imresize(img, (1:128, 1:128)) # 128*128
julia> imresize(img, (1:128, )) # 128*256
julia> imresize(img, 128) # 128*256
julia> imresize(img, ratio = 0.5) #128*128
julia> imresize(img, ratio = (2, 1)) # 256*128
julia> imresize(img, (128,128), method=Linear()) #128*128
julia> imresize(img, (128,128), method=BSpline(Linear())) #128*128
julia> imresize(img, (128,128), method=Lanczos4OpenCV()) #128*128

σ = map((o,n)->0.75*o/n, size(img), sz)
kern = KernelFactors.gaussian(σ)   # from ImageFiltering
imgr = imresize(imfilter(img, kern, NA()), sz)
```

詳細は[`restrict`](@ref)を参照してください。
