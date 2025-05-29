```
ProjectF(f, nl_max::Tuple{Int,Int}, radial_basis::RadialBasis; 
         dict=false, use_measurements=false, integ_method=:cubature,
         integ_params=(;))
```

Evaluates $\langle f | n \ell m \rangle$ at each $(n,\ell,m)$ up to  `nl_max = (n_max, l_max)` and returns the result as a `ProjectedF`.

`f` : Can be a `Function`, `f_uSph`, `GaussianF`, or `Vector{GaussianF}`.        `f_uSph` is preferred if your function has any symmetries, and is not        gaussian, as specifying those will greatly speed up evaluation.

`radial_basis` : Either a `Wavelet` or `Tophat`

`dict` : If true, returns an `FCoeffs` instead of a `ProjectedF`, which stores     the coefficients as a dictionary instead.

`use_measurements` : If `true`, will give the results as a measurement with     uncertainty given by the integration error.

`integ_method` : Either `:discrete`, `:cubature`, `:vegas`, or `:vegasmc`.     `:discrete` will use `SphericalHaarTransform` to do the transformation     with the two-point Gaussian quadrature method.

`integ_params` : keyword arguments to pass to the integrator. If `:cubature`,      these are kwargs for `hcubature`. If `:vegas` or `:vegasmc`, these are     kwargs for `MCIntegration`'s `integrate` method. Ignored if using     `:discrete`.
