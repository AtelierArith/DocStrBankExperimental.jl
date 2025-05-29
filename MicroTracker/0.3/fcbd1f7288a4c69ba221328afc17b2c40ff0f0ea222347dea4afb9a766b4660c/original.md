```
add_resolution_column!(particle_data::AbstractDataFrame)
```

Look at a frame of the video in `original_video` which corresponds to the data and add a column for the resolution of type Tuple{Int, Int}. Modifies `particle_data` in place, signfified by the `!` in the function name.

Uses [`getvideoresolution`](@ref).
