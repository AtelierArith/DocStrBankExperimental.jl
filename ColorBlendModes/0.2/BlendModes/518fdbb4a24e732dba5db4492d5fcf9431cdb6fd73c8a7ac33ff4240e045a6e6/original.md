```
BlendOverlay
```

This mode uses the [`multiply`](@ref BlendMultiply) or [`screen`](@ref BlendScreen) mode, depending on the backdrop color. The overlay mode is the inverse of the [`hard-light`](@ref BlendHardLight) mode.

```
    if Cb <= 0.5
        Cdest = Csrc × 2Cb
    else
        Cdest = 1 - ((1 - Csrc) × (1 - 2Cb))
    end
```
