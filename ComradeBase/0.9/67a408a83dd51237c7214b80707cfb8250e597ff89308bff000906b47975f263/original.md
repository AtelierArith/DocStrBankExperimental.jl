```
intensitymap!(img::AbstractIntensityMap, mode;, executor = SequentialEx())
```

Computes the intensity map or *image* of the `model`. This updates the `IntensityMap` object `img`.

Optionally the user can specify the `executor` that uses `FLoops.jl` to specify how the loop is done. By default we use the `SequentialEx` which uses a single-core to construct the image.
