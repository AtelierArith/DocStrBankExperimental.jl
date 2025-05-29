```
PiecewiseLinearTransiogram(abscissas, ordinates)
```

A piecewise-linear transiogram model with `abscissas` and matrix `ordinates` obtained from an [`EmpiricalTransiogram`](@ref).

```
PiecewiseLinearTransiogram(ball, abscissas, ordinates)
```

Alternatively, use a custom metric `ball`.

## References

  * Li, W. & Zhang, C. 2005. [Application of Transiograms to Markov Chain Simulation and Spatial Uncertainty Assessment of Land-Cover Classes](https://www.tandfonline.com/doi/abs/10.2747/1548-1603.42.4.297)
  * Li, W. & Zhang, C. 2010. [Linear interpolation and joint model fitting of experimental transiograms for Markov chain simulation of categorical spatial variables](https://www.tandfonline.com/doi/abs/10.1080/13658810903127991)
