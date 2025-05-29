```
noise_warp(img, noise_source::AbstractSampler; squared = true, variance = 0.1, crop = true)
```

`noise_warp` takes both an `img` and a `noise_source` built from `CoherentNoise.jl` and returns a warpped image. The principle is simple:

  * Two matrices of noise are generated using `noise_source`.
  * These matrices are converted into vector field by centering the values around 0

and scaling them with `variance * size`.

  * The vector field corresponds to the displacement of the pixels in the x/y coordinate field.
  * `ImageTransformations` apply the transformations and adaptively warp the image.
  * If `crop` is true, the image will be cropped to ensure no `NaN` values are contained.
