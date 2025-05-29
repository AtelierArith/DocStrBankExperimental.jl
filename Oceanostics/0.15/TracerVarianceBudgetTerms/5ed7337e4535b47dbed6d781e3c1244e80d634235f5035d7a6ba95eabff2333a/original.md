```julia
TracerVarianceDissipationRate(
    model,
    tracer_name;
    tracer,
    location
)

```

Return a `KernelFunctionOperation` that computes the isotropic variance dissipation rate for `tracer_name` in `model.tracers`. The isotropic variance dissipation rate is defined as 

```
    χ = 2 ∂ⱼc ⋅ Fⱼ
```

where `Fⱼ` is the diffusive flux of `c` in the `j`-th direction and `∂ⱼ` is the gradient operator. `χ` is implemented in its conservative formulation based on the equation above. 

Note that often `χ` is written as `χ = 2κ (∇c ⋅ ∇c)`, which is the special case for Fickian diffusion (`κ` is the tracer diffusivity).

Here `tracer_name` is needed even when passing `tracer` in order to get the appropriate `tracer_index`. When passing `tracer`, this function should be used as

```julia
grid = RectilinearGrid(size=(4, 4, 4), extent=(1, 1, 1))
model = NonhydrostaticModel(grid=grid, tracers=:b, closure=SmagorinskyLilly())

b̄ = Field(Average(model.tracers.b, dims=(1,2)))
b′ = model.tracers.b - b̄

χb = TracerVarianceDissipationRate(model, :b, tracer=b′)
```
