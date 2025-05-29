```
image = shepp_logan(M, [N,] [case] ; options...)
```

Convenience method for generating `M×N` samples of Shepp-Logan phantoms.

# In

  * `M::Int` : horizontal size
  * `N::Int` : vertical size, defaults to `M`
  * `case::EllipsePhantomVersion = SheppLogan()`

# Options

  * `oversample::Int = 3` (usually)
  * `yflip::Bool = true` (reverse `y` samples for convenience.)
  * `T::Type{<:Number}` default `Float32` (except `Int` for `BrainWeb` version)
  * `kwargs...` remaining options passed to `ellipse_parameters` for parameters.

# Out

  * `image` : `M × N` matrix

The default here is 3× over-sampling along both axes (9 samples per pixel), except for the `SheppLoganBrainWeb` phantom that consists of integer indices.
