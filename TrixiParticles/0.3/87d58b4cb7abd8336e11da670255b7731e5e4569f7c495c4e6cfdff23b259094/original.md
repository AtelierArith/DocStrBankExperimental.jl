```
PressureMirroring()
```

`density_calculator` for `BoundaryModelDummyParticles`.

!!! note
    This boundary model requires high viscosity for stability with WCSPH. It also produces significantly worse results than [`AdamiPressureExtrapolation`](@ref) and is not more efficient because smaller time steps are required due to more noise in the pressure. We added this model only for research purposes and for comparison with [SPlisHSPlasH](https://github.com/InteractiveComputerGraphics/SPlisHSPlasH).

