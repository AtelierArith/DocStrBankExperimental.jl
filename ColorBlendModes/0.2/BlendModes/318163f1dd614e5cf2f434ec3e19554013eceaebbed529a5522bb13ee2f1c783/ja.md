```
BlendSoftLight
```

結果は、[`hard-light`](@ref BlendHardLight) モードに似ていますが、より穏やかです。このモードは、[`overlay`](@ref BlendOverlay) モードにも関連しています。

ColorBlendModes は、以下に示すように W3C のドラフトの定義を使用しています。`soft-light` の定義は異なることに注意してください。

```
    if Csrc <= 0.5
        Cdest = Cb - (1 - 2Csrc) × Cb × (1 - Cb)
    else
        if Cb <= 0.25
            D = ((4Cb - 3) × Cb + 1) × 4Cb
        else
            D = sqrt(Cb)
        end
        Cdest = Cb + (2Csrc - 1) × (D - Cb)
    end
```
