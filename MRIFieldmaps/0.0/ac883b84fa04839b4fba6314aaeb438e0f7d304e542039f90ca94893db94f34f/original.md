```
finit = b0init(ydata, echotime; kwargs...)
```

Classic B0 field map estimation based on the phase difference of complex images at two different echo times. If sensitivity maps (`smap`) are provided, complex coil combination is done first. This code works with images of arbitrary dimensions (2D, 3D, etc.), and with multiple coils.

In the usual case where `echotime` has units of seconds, the returned B0 fieldmap will have units of Hz.

If `df` is nonempty (which always holds for water-fat case), then perform discrete maximum-likelihood estimation using `fdict`.

# In

  * `ydata (dims..., nc, ne)` `ne` sets of complex images for `nc ≥ 1` coils
  * `echotime (ne)` vector of `ne ≥ 2` echo times (only first 2 are used)

# Options

  * `smap (dims..., nc)` complex coil maps; default `nothing`
  * `threshold` set `finit` values where `|y1| < threshold * max(|y1|)`  to the mean of the "good" values where `|y1| ≥ threshold * max(|y1|)`.  default: `0.1`

# Options for water-fat case:

  * `df` Δf values in water-fat imaging (def: `[]`) units Hz, e.g., `[440]` at 3T
  * `relamp` relative amplitudes in multi-species water-fat (def: `[]`)
  * `fband` frequency bandwidth for `fdict; default`floor(1 / minimum(echo time spacing))`
  * `nf` number of discrete frequencies to try; default `1+floor(fband)` so ≈1Hz spacing
  * `fdict` "dictionary" of discrete frequency values to try; default `LinRange(-1/2,1/2,nf) * fband`

# Out

  * `finit` initial B0 fieldmap estimate in Hz
