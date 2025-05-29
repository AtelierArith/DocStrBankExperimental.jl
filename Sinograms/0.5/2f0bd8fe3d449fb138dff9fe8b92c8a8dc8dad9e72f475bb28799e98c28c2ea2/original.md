```
fbp!(image, sino ; orbit::Real = 180, kwargs...)
```

FBP reconstruction from a parallel-beam sinogram of size `[nr × nϕ]`. Writes result into `image` matrix.

# Input

  * `sino::AbstractMatrix`

# Options for `SinoPar` constructor

  * `dr` : sinogram radial spacing; default 1
  * `orbit` : angular range in degrees; default 180
  * `orbit_start` : angular range in degrees; default 0

# Options for `ImageGeom`

  * `dx`, `dy`, `deltas`, `offset_x`, `offset_y`, `offsets`
  * `rmax` maximum radius for mask

# Options

  * `kwargs` : passed to `plan_fbp`

# Output

  * `image::AbstractMatrix` is mutated
