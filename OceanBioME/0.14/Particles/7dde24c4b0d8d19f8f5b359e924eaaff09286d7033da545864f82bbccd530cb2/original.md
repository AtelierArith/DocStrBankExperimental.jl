```
BiogeochemicalParticles(number; 
                        grid,
                        biogeochemistry,
                        advection = LagrangianAdvection(),
                        timestepper = ForwardEuler,
                        field_interpolation = NearestPoint(),
                        scalefactors = ones(number))
```

Creates `number` particles with `biogeochemistry` on `grid`, advected by `advection` which defaults to `LagrangianAdvection` (i.e. they comove with the water). The biogeochemistry is stepped by `timestepper` and tracer fields are interpolated by `field_interpolation`, which defaults to directly reading the nearest center point and taking up/depositing in the same.

Particles can also have a `scalefactor` which scales their tracer interaction (e.g. to mimic the particle representing multiple particles).
