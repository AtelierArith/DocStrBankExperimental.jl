```
smooth!(out::GenericImage, img::GenericImage, fₛ::AbstractImageSmoothAlgorithm, args...; kwargs...)
```

アルゴリズム `fₛ` を使用して `img::GenericImage` をスムーズにします。

# 出力

`out` はインプレースで変更されます。

# 例

アルゴリズムを `smooth!` に単純に渡します：

```julia
# まずアルゴリズムインスタンスを生成します
fₛ = L0Smooth()

## グレイまたはRGB画像用
imgₛ = similar(img)

smooth!(imgₛ, img, fₛ)
```

参照： [`smooth`](@ref) ```
