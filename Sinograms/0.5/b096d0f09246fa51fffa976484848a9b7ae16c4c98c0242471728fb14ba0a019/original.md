```
plan = plan_fbp(rg, ig; window=Window(), ...)
```

Plan FDK 3D CBCT image reconstruction, with either flat or arc detector.

To use this method, you first call it with the CT geometry and image geometry. The routine returns the initialized `plan`. Thereafter, to to perform FDK reconstruction, call `fbp` with the `plan` (perhaps numerous times for the same geometry).

# in

  * `rg::CtGeom`
  * `ig::ImageGeom` only reconstruct pixels within `ig.mask`.

# option

  * `window::Window` e.g., `Window(Hamming(), 0.8)`; default `Window()`
  * `npad::Int` # of radial bins after padding; default `nextpow(2, rg.ns + 1)`
  * `decon1::Bool` deconvolve interpolator effect? (default `true`)

# out

  * `plan::FDKplan` initialized plan
