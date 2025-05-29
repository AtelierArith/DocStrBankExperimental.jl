```
ColorMixture((rgb₁, rgb₂, ...), (i₁, i₂, ...))
ColorMixture((rgb₁, rgb₂, ...), i₁, i₂, ...)
ColorMixture{T}(...)                       # 強度を要素型に強制変換
```

定義されたRGBへの変換を持つマルチチャンネルカラーを表します。`rgbⱼ`はチャンネル`j`に対応するRGBカラーであり、その強度は`iⱼ`です。色は強度加重を使用してRGBに変換されます: `rgb = sum(ivalues .* rgbvalues)`。

[`MultiChannelColor`](@ref)は、`rgb`リストを必要とせず、RGBへの組み込み変換がない代替手段です。
