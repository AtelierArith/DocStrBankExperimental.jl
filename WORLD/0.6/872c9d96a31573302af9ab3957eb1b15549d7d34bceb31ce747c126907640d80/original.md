```julia
dio(x, fs)
dio(x, fs, opt)

```

Dio estimates F0 trajectory given a monoral input signal.

**Paremters**

  * `x`  : Input signal
  * `fs` : Sampling frequency
  * `opt` : DioOption

**Returns**

  * `time_axis`  : Temporal positions.
  * `f0`         : F0 contour.
