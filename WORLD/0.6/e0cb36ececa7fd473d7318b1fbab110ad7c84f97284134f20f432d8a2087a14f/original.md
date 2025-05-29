```julia
harvest(x, fs)
harvest(x, fs, opt)

```

Harvest estimates F0 trajectory given a monoral input signal.

**Paremters**

  * `x`  : Input signal
  * `fs` : Sampling frequency
  * `opt` : HarvestOption

**Returns**

  * `time_axis`  : Temporal positions.
  * `f0`         : F0 contour.
