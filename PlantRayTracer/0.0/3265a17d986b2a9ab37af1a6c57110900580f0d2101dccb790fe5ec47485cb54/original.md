```
RTSettings(;verbose = true, parallel = false, pkill = 0.2, maxiter = 2,
            sampler = Random.Xoshiro(123456789), nx = 3, ny = 3, nz = 0, dx = 0.0,
            dy = 0.0, dz = 0.0)
```

Settings for the ray tracer:

  * `verbose` indicates if the ray tracer will print warnings and other information.
  * `parallel` indicates if the raytracer will run on a single core or make use of multiple

cores in the machine based on Julia's multithreading support. `pkill` is the probably that a ray is terminated by the Russian roulette after it has been scattered a `maxiter` number of times (this excludes interactions with materials of type `Sensor`).

  * `sampler` is the pseudo-random number generator to be used by the ray tracer.
  * `nx` and `ny` are the number of times the mesh will be cloned by the grid cloner in each

direction along the x and y axis (e.g., setting `nx = 1` and `ny = 1` will generate a grid of 3 x 3 clones of the original mesh), whereas `dx` and `dy` will be distance at which each new clone will be generated (along the axis).

  * `nz` is the number of times the mesh will be cloned in the vertical direction. Unlike

horizontal cloning, the vertical cloning is always done in the positive direction of `z` axis and the number of clones will be exactly `nz`.

See VPL documentation for more details on the ray  tracer.

## Examples

```jldoctest
julia> RTSettings(parallel = true, maxiter = 3);
```
