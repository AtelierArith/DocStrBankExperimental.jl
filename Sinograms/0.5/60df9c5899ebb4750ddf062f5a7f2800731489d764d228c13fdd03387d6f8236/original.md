```
plan = plan_fbp(rg, ig; how=:normal, window=Window())
```

Plan FBP 2D tomographic image reconstruction for parallel-beam & fan-beam cases, with either flat or arc detector for fan-beam case.

To use this method, you first call it with the sinogram geometry and image geometry. The routine returns the initialized `plan`. Thereafter, to to perform FBP reconstruction, call `fbp` with the `plan` (perhaps numerous times for the same geometry).

# in

  * `rg::SinoGeom`
  * `ig::ImageGeom` only reconstruct pixels within `ig.mask`.

# option

  * `how::Symbol` how to reconstruct

      * `:normal` default
      * `:mojette` use mojette rebinning and Gtomo2_table
  * `window::Window` e.g., `Window(Hamming(), 0.8)`; default `Window()`
  * `npad::Int` # of radial bins after padding; default `nextpow(2, rg.nb + 1)`
  * `decon1::Bool` deconvolve interpolator effect? (default `true`)
  * `T::Type{<:Number}` type of `sino` elements (default `Float32`)

# out

  * `plan::FBPplan` initialized plan
