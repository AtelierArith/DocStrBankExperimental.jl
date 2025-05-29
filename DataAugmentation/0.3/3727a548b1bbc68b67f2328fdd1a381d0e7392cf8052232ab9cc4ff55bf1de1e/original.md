```
Normalize(means, stds)
```

Normalizes the last dimension of an `AbstractArrayItem{N}`.

Supports `apply!`.

## Examples

Preprocessing a 3D image with 3 color channels.

{cell=Normalize}

```julia
using DataAugmentation, Images
image = Image(rand(RGB, 20, 20, 20))
tfms = ImageToTensor() |> Normalize((0.1, -0.2, -0.1), (1,1,1.))
apply(tfms, image)
```
