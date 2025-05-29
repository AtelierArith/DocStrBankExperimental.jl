```
BlendHardLight
```

This mode uses the [`multiply`](@ref BlendMultiply) or [`screen`](@ref BlendScreen) mode, depending on the source color. The overlay mode is the inverse of the [`overlay`](@ref BlendOverlay) mode.

```
    if Csrc <= 0.5
        Cdest = Cb × 2Csrc
    else
        Cdest = 1 - ((1 - Cb) × (1 - 2Csrc))
    end
```
