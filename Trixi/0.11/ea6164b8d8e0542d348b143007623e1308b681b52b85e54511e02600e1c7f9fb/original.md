```
DGMulti(; polydeg::Integer,
          element_type::AbstractElemShape,
          approximation_type=Polynomial(),
          surface_flux=flux_central,
          surface_integral=SurfaceIntegralWeakForm(surface_flux),
          volume_integral=VolumeIntegralWeakForm(),
          RefElemData_kwargs...)
```

Create a discontinuous Galerkin method which uses

  * approximations of polynomial degree `polydeg`
  * element type `element_type` (`Tri()`, `Quad()`, `Tet()`, and `Hex()` currently supported)

Optional:

  * `approximation_type` (default is `Polynomial()`; `SBP()` also supported for `Tri()`, `Quad()`, and `Hex()` element types).
  * `RefElemData_kwargs` are additional keyword arguments for `RefElemData`, such as `quad_rule_vol`. For more info, see the [StartUpDG.jl docs](https://jlchan.github.io/StartUpDG.jl/dev/).
