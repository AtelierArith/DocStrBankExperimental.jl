```julia
struct CollisionData{R<:Real}
```

Struct which stores the collision information about two bodies in 2-dimensional space.

# Fields

  * `separation::R`: If the bodies do not intersect, this is the shortest distance between any two points on their boundaries. If the bodies intersect, this is the negative of the minimum displacement magnitude required to separate them.
  * `direction::SVector{2,R}`: Unit vector. If the bodies do not intersect, this is the direction of the minimum distance vector from body `A` to body `B`. If the bodies intersect, this is the direction to displace body `B` to separate them.
