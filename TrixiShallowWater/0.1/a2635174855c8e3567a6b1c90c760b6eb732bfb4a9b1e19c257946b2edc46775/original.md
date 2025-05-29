```
IndicatorHennemannGassnerShallowWater(equations::AbstractEquations, basis;
                                      alpha_max=0.5,
                                      alpha_min=0.001,
                                      alpha_smooth=true,
                                      variable)
```

Modified version of the [`Trixi.IndicatorHennemannGassner`](@extref) indicator used for shock-capturing for shallow water equations. After the element-wise values for the blending factors are computed an additional check is made to see if the element is partially wet. In this case, partially wet elements are set to use the pure finite volume scheme that is guaranteed to be well-balanced for this wet/dry transition state of the flow regime.

See also [`Trixi.VolumeIntegralShockCapturingHG`](@extref).

## References

  * Hennemann, Gassner (2020) "A provably entropy stable subcell shock capturing approach for high order split form DG" [arXiv: 2008.12044](https://arxiv.org/abs/2008.12044)
