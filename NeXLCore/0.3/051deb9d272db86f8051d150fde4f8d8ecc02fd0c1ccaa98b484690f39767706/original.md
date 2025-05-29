```
stage2image(::Type{DefaultStageMapping}, stage_coord::Dict{Symbol,Any}, centered_coord::Dict{Symbol,Any}, theta::Float64)
```

`stage2image(...)` is the inverse function of `image2stage(...)`.  Given the stage coordinate of the center of the image  `stage_coord` and the stage coordinate that would center the pixel of interest `centered_coord`, compute the pixel coordinate corresponding to the `centered_coordinate` when the stage is at `stage_coord`.
