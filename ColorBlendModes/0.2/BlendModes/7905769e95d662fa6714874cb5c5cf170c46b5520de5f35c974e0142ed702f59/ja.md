```
BlendHardLight
```

このモードは、ソースカラーに応じて[`multiply`](@ref BlendMultiply)モードまたは[`screen`](@ref BlendScreen)モードを使用します。オーバーレイモードは[`overlay`](@ref BlendOverlay)モードの逆です。

```
    if Csrc <= 0.5
        Cdest = Cb × 2Csrc
    else
        Cdest = 1 - ((1 - Cb) × (1 - 2Csrc))
    end
```
