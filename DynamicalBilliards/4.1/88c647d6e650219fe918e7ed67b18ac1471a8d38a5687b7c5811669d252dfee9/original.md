```
Wall{T<:AbstractFloat} <: Obstacle{T}
```

Wall obstacle supertype.

All `Wall` subtypes (except `PeriodicWall`) can be called as `Wall(sp, ep)`, in which case the normal vector is computed automatically to point to the left of `v = ep - sp`.
