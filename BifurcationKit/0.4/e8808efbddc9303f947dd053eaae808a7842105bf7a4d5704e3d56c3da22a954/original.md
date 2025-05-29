```
Multiple Tangent continuation algorithm.
```

The predictor is designed [Uecker2014] to avoid spurious branch switching and pass singular points especially in PDE where branch point density can be quite high. It is called `pmcont` in `pde2path`.

  * `alg::BifurcationKit.PALC`: Tangent predictor used Default: PALC()
  * `τ::Any`: Save the current tangent
  * `α::Real`: Damping in Newton iterations, 0 < α < 1
  * `nb::Int64`: Number of predictors
  * `currentind::Int64`: Index of the largest converged predictor Default: 0
  * `pmimax::Int64`: Index for lookup in residual history Default: 1
  * `imax::Int64`: Maximum index for lookup in residual history Default: 4
  * `dsfact::Real`: Factor to increase ds upon successful step Default: 1.5

# Constructor(s)

```
Multiple(alg, x0, α, n)

Multiple(pred, x0, α, n)

Multiple(x0, α, n)
```
