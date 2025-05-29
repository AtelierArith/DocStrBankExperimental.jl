```
image2stage(::Type{DefaultStageMapping}, stage_coord::Dict{Symbol,Any}, img_coord::Dict{Symbol,Any}, theta::Float64)
```

Given the stage coordinate at the center of the image `stage_coord`, the pixel coordinate of interest (in the same units as `stage_coord`) and the image rotation `theta`, compute the stage coordinate that would bring the pixel into the center of the image. 
