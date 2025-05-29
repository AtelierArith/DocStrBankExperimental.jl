```julia
ErtelPotentialVorticity(model; tracer, location)

```

Calculate the Ertel Potential Vorticty for `model`, where the characteristics of the Coriolis rotation are taken from `model.coriolis`. The Ertel Potential Vorticity is defined as

```
EPV = ωₜₒₜ ⋅ ∇b
```

where ωₜₒₜ is the total (relative + planetary) vorticity vector, `b` is the buoyancy and ∇ is the gradient operator.

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(topology = (Flat, Flat, Bounded), size = 4, extent = 1);

julia> N² = 1e-6;

julia> b_bcs = FieldBoundaryConditions(top=GradientBoundaryCondition(N²));

julia> model = NonhydrostaticModel(; grid, coriolis=FPlane(1e-4), buoyancy=BuoyancyTracer(), tracers=:b, boundary_conditions=(; b=b_bcs));

julia> stratification(z) = N² * z;

julia> set!(model, b=stratification)

julia> using Oceanostics: ErtelPotentialVorticity

julia> EPV = ErtelPotentialVorticity(model)
KernelFunctionOperation at (Face, Face, Face)
├── grid: 1×1×4 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── kernel_function: ertel_potential_vorticity_fff (generic function with 1 method)
└── arguments: ("1×1×4 Field{Face, Center, Center} on RectilinearGrid on CPU", "1×1×4 Field{Center, Face, Center} on RectilinearGrid on CPU", "1×1×5 Field{Center, Center, Face} on RectilinearGrid on CPU", "1×1×4 Field{Center, Center, Center} on RectilinearGrid on CPU", "0", "0", "0.0001")

julia> interior(compute!(Field(EPV)))
1×1×5 view(::Array{Float64, 3}, 1:1, 1:1, 4:8) with eltype Float64:
[:, :, 1] =
 0.0

[:, :, 2] =
 1.0000000000000002e-10

[:, :, 3] =
 9.999999999999998e-11

[:, :, 4] =
 1.0000000000000002e-10

[:, :, 5] =
 1.0e-10
```

Note that EPV values are correctly calculated both in the interior and the boundaries. In the interior and top boundary, EPV = f×N² = 10⁻¹⁰, while EPV = 0 at the bottom boundary since ∂b/∂z is zero there.
