```
PlanetRelAstromLikelihood(
    (epoch = 5000, ra = -505.7637580573554, dec = -66.92982418533026, σ_ra = 10, σ_dec = 10, cor=0),
    (epoch = 5050, ra = -505.7637580573554, dec = -66.92982418533026, σ_ra = 10, σ_dec = 10, cor=0),
    (epoch = 5100, ra = -505.7637580573554, dec = -66.92982418533026, σ_ra = 10, σ_dec = 10, cor=0),
)
```

Represents a likelihood function of relative astometry between a host star and a secondary body. `:epoch` is a required column, in addition to either `:ra`, `:dec`, `:σ_ra`, `:σ_dec` or `:pa`, `:sep`, `:σ_pa`, `:σ_sep`. All units are in **milliarcseconds** or **radians** as appropriate.

In addition to the example above, any Tables.jl compatible source can be provided.
