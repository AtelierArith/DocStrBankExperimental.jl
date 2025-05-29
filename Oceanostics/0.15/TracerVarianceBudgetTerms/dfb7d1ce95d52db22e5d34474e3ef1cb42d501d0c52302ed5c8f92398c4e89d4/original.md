```julia
TracerVarianceTendency(model, tracer_name; location)

```

Return a `KernelFunctionOperation` that computes the tracer variance tendency:

```
TEND = 2 c ∂ₜc
```

where `c` is the tracer and `∂ₜc` is the tracer tendency (computed using Oceananigans' tracer tendency kernel).

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size = (1, 1, 4), extent = (1, 1, 1));

julia> model = NonhydrostaticModel(; grid, tracers=:b);

julia> using Oceanostics.TracerVarianceBudgetTerms: TracerVarianceTendency

julia> χ = TracerVarianceTendency(model, :b)
KernelFunctionOperation at (Center, Center, Center)
├── grid: 1×1×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×1×3 halo
├── kernel_function: c∂ₜcᶜᶜᶜ (generic function with 1 method)
└── arguments: ("Val{1}", "Val{:b}", "Centered(order=2)", "Nothing", "FluxBoundaryCondition: Nothing", "Nothing", "Nothing", "(velocities=(u=ZeroField{Int64}, v=ZeroField{Int64}, w=ZeroField{Int64}), tracers=(b=ZeroField{Int64},))", "(u=1×1×4 Field{Face, Center, Center} on RectilinearGrid on CPU, v=1×1×4 Field{Center, Face, Center} on RectilinearGrid on CPU, w=1×1×5 Field{Center, Center, Face} on RectilinearGrid on CPU)", "(b=1×1×4 Field{Center, Center, Center} on RectilinearGrid on CPU,)", "NamedTuple()", "Nothing", "Clock{Float64, Float64}(time=0 seconds, iteration=0, last_Δt=Inf days)", "zeroforcing (generic function with 1 method)")
```
