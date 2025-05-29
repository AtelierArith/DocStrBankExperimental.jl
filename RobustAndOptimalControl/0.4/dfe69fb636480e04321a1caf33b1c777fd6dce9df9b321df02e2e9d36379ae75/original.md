```
centers, radii = fit_complex_perturbations(P, w; relative=true, nominal=:mean)
```

For each frequency in `w`, fit a circle in the complex plane that contains all models in the model set `P`, represented as an `LTISystem` with `Particles` coefficients. Note, the resulting radii can be quite unstable if the number of particles is small, in particular if the particles are normally distributed instead of uniformly.

If `realtive = true`, circles encompassing `|(P - Pn)/Pn|` will be returned (multiplicative/relative uncertainty). If `realtive = false`, circles encompassing `|P - Pn|` will be returned (additive uncertainty).

If `nominal = :mean`, the mean of `P` will be used as nominal model. If `nominal = :first`, the first particle will be used. See `MonteCarloMeasurements.with_nominal` to set the nominal value in the first particle. If `nominal = :center`, the middle point `(pmaximum(ri)+pminimum(ri))/2` will be used. This typically gives the smallest circles.

See also [`nyquistcircles`](@ref) to plot circles (only if relative=false).
