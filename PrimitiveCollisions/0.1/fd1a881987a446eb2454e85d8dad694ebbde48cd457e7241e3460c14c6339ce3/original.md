```julia
function invert(coldata::CollisionData{R}, current_state::State{R}) where {R}
```

Given collision data in the `current_state` frame of reference, transform it into the opposite frame of reference.
