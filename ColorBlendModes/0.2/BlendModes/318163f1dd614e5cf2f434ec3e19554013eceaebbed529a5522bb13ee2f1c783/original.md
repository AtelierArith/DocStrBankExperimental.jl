```
BlendSoftLight
```

The result is similar to the [`hard-light`](@ref BlendHardLight) mode, but milder. This mode is also related to the [`overlay`](@ref BlendOverlay) mode.

ColorBlendModes uses the definition of W3C drafts as shown below. Note that there are different definitions of the `soft-light`.

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
