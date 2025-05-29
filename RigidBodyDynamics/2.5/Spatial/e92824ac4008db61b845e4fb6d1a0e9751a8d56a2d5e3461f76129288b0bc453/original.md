```julia
point_acceleration(twist, accel, point)

```

Given the twist $dot{T}_{j}^{k,i}$ of frame $j$ with respect to frame $i$, expressed in frame $k$ and its time derivative (a spatial acceleration), as well as the location of a point fixed in frame $j$, also expressed in frame $k$, compute the acceleration of the point relative to frame $i$.
