```
from_bcoords(ξ, sφ, o::Obstacle) -> pos, vel
```

Convert the boundary coordinates `ξ, sφ` on the obstacle to real coordinates `pos, vel`.

Note that `vel` always points away from the obstacle.

This function is the inverse of [`to_bcoords`](@ref).
