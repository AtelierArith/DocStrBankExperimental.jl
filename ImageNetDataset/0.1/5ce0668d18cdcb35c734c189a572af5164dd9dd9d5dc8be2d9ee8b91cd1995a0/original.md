```
RandomCropNormalize([; output_size, open_size, mean, std])
```

Preprocessing pipeline crops an input image to `output_size` at a random position and normalizes it according to `mean` and `std`. Returns an array in WHC format `(width, height, channels)`.

Applied using [`transform`](@ref) and [`inverse_transform`](@ref).

## Keyword arguments:

  * `output_size`: Output size `(width, height)` of the center-crop. Defaults to `(224, 224)`.
  * `open_size`: Preferred size `(width, height)` to open the image in using JpegTurbo. Defaults to `(256, 256)`
  * `mean`: Mean of the normalization over color channels. Defaults to `(0.485f0, 0.456f0, 0.406f0)`.
  * `std`: Standard deviation of the normalization over color channels Defaults to `(0.229f0, 0.224f0, 0.225f0)`.
