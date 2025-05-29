```
BLAKJac_defaults!(trajectorySet::Vector{<:Vector{<:TrajectoryElement}}, options::Dict)
```

Initializes the elements of the dictionary 'options' (if not already filled in) to meaningful default values. 

A trajectorySet is required as input (see the `TrajectorySet` function), which defines the number of profiles (nTR) as well as the ky and kz ranges.
