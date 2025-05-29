```
ブレンドオーバーレイ
```

このモードは、バックドロップの色に応じて[`multiply`](@ref BlendMultiply)または[`screen`](@ref BlendScreen)モードを使用します。オーバーレイモードは[`hard-light`](@ref BlendHardLight)モードの逆です。

```
    if Cb <= 0.5
        Cdest = Csrc × 2Cb
    else
        Cdest = 1 - ((1 - Csrc) × (1 - 2Cb))
    end
```
