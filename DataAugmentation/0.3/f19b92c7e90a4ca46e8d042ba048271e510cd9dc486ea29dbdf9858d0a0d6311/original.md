```
PermuteDims(perm)
```

Permute the dimensions of an `ArrayItem`. `perm` is a vector or a tuple specifying the permutation, whose length has to match the dimensionality of the `ArrayItem`s data.

Refer to the `permutedims` documentation for examples of permutation vectors `perm`.

Supports `apply!`.

## Examples

Preprocessing an image with 3 color channels.

{cell=PermuteDims}

```julia
using DataAugmentation, Images
image = Image(rand(RGB, 20, 20))

# Turn image to tensor and permute dimensions 2 and 1
# to convert HWC (height, width, channel) array to WHC (width, height, channel)
tfms = ImageToTensor() |> PermuteDims(2, 1, 3)
apply(tfms, image)
```
