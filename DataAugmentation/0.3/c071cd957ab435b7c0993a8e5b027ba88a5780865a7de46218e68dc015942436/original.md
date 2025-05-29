```
ImageToTensor()
```

Expands an `Image{N, T}` of size `(height, width, ...)` to an `ArrayItem{N+1}` with size `(width, height, ..., ch)` where `ch` is the number of color channels of `T`.

Supports `apply!`.

## Examples

{cell=ImageToTensor}

```julia
using DataAugmentation, Images

h, w = 40, 50
image = Image(rand(RGB, h, w))
tfm = ImageToTensor()
apply(tfm, image) # ArrayItem in WHC format of size (50, 40, 3)
```
