```julia
TracerVarianceDiffusiveTerm(model, tracer_name; location)

```

Return a `KernelFunctionOperation` that computes the diffusive term of the tracer variance prognostic equation using Oceananigans' diffusive tracer flux divergence kernel:

```
    DIFF = 2 c ∂ⱼFⱼ
```

where `c` is the tracer, and `Fⱼ` is the tracer's diffusive flux in the `j`-th direction.

```julia
grid = RectilinearGrid(size=(4, 4, 4), extent=(1, 1, 1))
model = NonhydrostaticModel(grid=grid, tracers=:b, closure=SmagorinskyLilly())

DIFF = TracerVarianceDiffusiveTerm(model, :b)
```
