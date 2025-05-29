```
find_trajectory_bounds(df_1particle::AbstractDataFrame, video_resolution::Tuple{Int, Int})
```

Return a tuple of frame numbers, `(low, high)` where all trajectory points are in bounds.

This calculates the radius of the particle, then iterates forward and backward from the center of the trajectory until it finds a point that is out of bounds. This is the high and low bound of the trajectory.
