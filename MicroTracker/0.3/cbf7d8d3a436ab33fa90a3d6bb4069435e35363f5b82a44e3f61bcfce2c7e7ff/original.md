```
clip_trajectory_edges(linked_data::AbstractDataFrame, linking_settings::NamedTuple)
```

Iterate through each trajectory and remove the tracking data where the particle is out of frame.

The particle is out of frame when the center is within the radius of the particle from the edge of the video.

Uses [`find_trajectory_bounds`](@ref) to find the bounds of the trajectory with [`inbounds`](@ref).
