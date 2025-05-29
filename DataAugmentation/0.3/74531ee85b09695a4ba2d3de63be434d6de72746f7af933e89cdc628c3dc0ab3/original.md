```
AdjustContrast(factor = 0.2)
AdjustContrast(distribution)
```

Adjust the contrast of an image by a factor chosen uniformly from `f ∈ [1-δ, 1+δ]`.

Pixels `c` are transformed `c + μ*(1-f)` where `μ` is the mean color of the image.

You can also pass any `Distributions.Sampleable` from which the factor is selected.

Pixels are clamped to [0,1] unless `clamp=false` is passed.

## Example

```julia
using DataAugmentation, TestImages

item = Image(testimage("lighthouse"))
tfm = AdjustContrast(0.2)
titems = [apply(tfm, item) for _ in 1:8]
showgrid(titems; ncol = 4, npad = 16)
```
