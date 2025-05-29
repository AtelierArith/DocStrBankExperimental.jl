```
params = disk_phantom_params( ; ...)
```

Generate `ndisk` ellipse phantom parameter 6-tuples for a head-sized disk plus many disks within it, designed so that the disks have some minimum separation `minsep` to avoid overlap and to simplify patch-based model fitting.

# Options

  * `fov::Real = 240` image field of view in mm
  * `rhead::Function = () -> 100` background radius for "head" [mm]
  * `muhead::Function = () -> 1000` "μ" (intensity) value for background head disk
  * `rdisk::Function = () -> 10 + 10 * rand()` random disk radii [10,20]
  * `mudisk::Function = () -> 100 + 200 * rand()` "μ" values for disks [100,300]
  * `ndisk::Function = () -> 10` # of random disks
  * `minsep::Real = 8` minimum disk separation in mm
  * `maxtry::Int = 500` give up on adding more disks if this is reached
  * `warn::Bool = false` warn if maxtry reached?
  * `seed::Int = 0` if nonzero then use this seed

The function options can be replaced with rand() for other Distributions.
