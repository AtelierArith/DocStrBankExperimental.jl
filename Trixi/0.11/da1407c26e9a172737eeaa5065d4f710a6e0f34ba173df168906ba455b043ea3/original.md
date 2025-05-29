```
IndicatorHennemannGassner(equations::AbstractEquations, basis;
                          alpha_max=0.5,
                          alpha_min=0.001,
                          alpha_smooth=true,
                          variable)
IndicatorHennemannGassner(semi::AbstractSemidiscretization;
                          alpha_max=0.5,
                          alpha_min=0.001,
                          alpha_smooth=true,
                          variable)
```

Indicator used for shock-capturing (when passing the `equations` and the `basis`) or adaptive mesh refinement (AMR, when passing the `semi`).

See also [`VolumeIntegralShockCapturingHG`](@ref).

## References

  * Hennemann, Gassner (2020) "A provably entropy stable subcell shock capturing approach for high order split form DG" [arXiv: 2008.12044](https://arxiv.org/abs/2008.12044)
