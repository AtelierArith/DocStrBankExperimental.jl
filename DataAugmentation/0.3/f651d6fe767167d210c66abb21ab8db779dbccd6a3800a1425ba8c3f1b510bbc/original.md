```
AdjustBrightness(δ = 0.2)
AdjustBrightness(distribution)
```

Adjust the brightness of an image by a factor chosen uniformly from `f ∈ [1-δ, 1+δ]` by multiplying each color channel by `f`.

You can also pass any `Distributions.Sampleable` from which the factor is selected.

Pixels are clamped to [0,1] unless `clamp=false` is passed.

## Example

```julia
using DataAugmentation, TestImages

item = Image(testimage("lighthouse"))
tfm = AdjustBrightness(0.2)
titems = [apply(tfm, item) for _ in 1:8]
showgrid(titems; ncol = 4, npad = 16)
```
