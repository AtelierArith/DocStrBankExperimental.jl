```
smooth(img, fₛ::AbstractImageSmoothAlgorithm, args...; kwargs...)
```

アルゴリズム `fₛ` を使用して `img` を平滑化します。

# 出力

返される画像 `imgₛ` は、`Gray` 画像の場合は `Array{Gray{N0f8}}` であり、`RGB` 画像の場合は `Array{RGB{N0f8}}` です。

# 例

入力画像とアルゴリズムを `smooth` に渡すだけです。

```julia
fₛ = L0Smooth()

imgₛ = smooth(img, fₛ)
```

これは「平滑化アルゴリズム `fₛ` を使用して画像 `img` を `smooth` する」と読み取れます。

インプレース平滑化については [`smooth!`](@ref) を参照してください。
