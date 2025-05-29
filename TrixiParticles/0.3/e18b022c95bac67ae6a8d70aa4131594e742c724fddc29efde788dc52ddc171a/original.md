```
AdamiPressureExtrapolation(; pressure_offset=0, allow_loop_flipping=true)
```

`density_calculator` for `BoundaryModelDummyParticles`.

# Keywords

  * `pressure_offset=0`: Sometimes it is necessary to artificially increase the boundary pressure                      to prevent penetration, which is possible by increasing this value.
  * `allow_loop_flipping=true`: Allow to flip the loop order for the pressure extrapolation.                             Disable to prevent error variations between simulations with                             different numbers of threads.                             Usually, the first (multithreaded) loop is over the boundary                             particles and the second loop over the fluid neighbors.                             When the number of boundary particles is larger than                             `ceil(0.5 * nthreads())` times the number of fluid particles,                             it is usually more efficient to flip the loop order and loop                             over the fluid particles first.                             The factor depends on the number of threads, as the flipped                             loop is not thread parallelizable.                             This can cause error variations between simulations with                             different numbers of threads.
