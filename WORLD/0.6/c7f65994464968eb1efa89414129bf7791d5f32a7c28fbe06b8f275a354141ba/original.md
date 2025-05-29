```julia
stonemask(x, fs, timeaxis, f0)

```

StoneMask refines the estimated F0 by Dio,

**Parameters**

  * `x` : Input signal
  * `fs` : Sampling frequency
  * `time_axis` : Temporal information
  * `f0` : f0 contour

**Returns**

  * `refined_f0` : Refined F0
