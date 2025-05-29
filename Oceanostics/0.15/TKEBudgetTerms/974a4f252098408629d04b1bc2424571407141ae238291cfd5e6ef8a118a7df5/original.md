```julia
PressureRedistributionTerm(
    model;
    velocities,
    pressure,
    location
)

```

Return a `KernelFunctionOperation` that computes the pressure redistribution term:

```
PR = uᵢ∂ᵢp
```

where `p` is the pressure. By default `p` is taken to be the total pressure (nonhydrostatic + hydrostatic):

```jldoctest ∇u⃗p_example
julia> using Oceananigans

julia> grid = RectilinearGrid(size = (1, 1, 4), extent = (1,1,1));

julia> model = NonhydrostaticModel(grid=grid);

julia> using Oceanostics.TKEBudgetTerms: PressureRedistributionTerm

julia> ∇u⃗p = PressureRedistributionTerm(model)
KernelFunctionOperation at (Center, Center, Center)
├── grid: 1×1×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×1×3 halo
├── kernel_function: uᵢ∂ᵢpᶜᶜᶜ (generic function with 1 method)
└── arguments: ("(u=1×1×4 Field{Face, Center, Center} on RectilinearGrid on CPU, v=1×1×4 Field{Center, Face, Center} on RectilinearGrid on CPU, w=1×1×5 Field{Center, Center, Face} on RectilinearGrid on CPU)", "1×1×4 Field{Center, Center, Center} on RectilinearGrid on CPU")
```

We can also pass `velocities` and `pressure` keywords to perform more specific calculations. The example below illustrates calculation of the nonhydrostatic contribution to the pressure redistrubution term:

```jldoctest ∇u⃗p_example
julia> ∇u⃗pNHS = PressureRedistributionTerm(model, pressure=model.pressures.pNHS)
KernelFunctionOperation at (Center, Center, Center)
├── grid: 1×1×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×1×3 halo
├── kernel_function: uᵢ∂ᵢpᶜᶜᶜ (generic function with 1 method)
└── arguments: ("(u=1×1×4 Field{Face, Center, Center} on RectilinearGrid on CPU, v=1×1×4 Field{Center, Face, Center} on RectilinearGrid on CPU, w=1×1×5 Field{Center, Center, Face} on RectilinearGrid on CPU)", "1×1×4 Field{Center, Center, Center} on RectilinearGrid on CPU")
```
