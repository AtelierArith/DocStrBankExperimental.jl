```julia
KineticEnergyTendency(model; location)

```

非静水圧寄与を除外したKEの傾向uᵢGᵢを計算する`KernelFunctionOperation`を返します：

```
KET = ½∂ₜuᵢ² = uᵢGᵢ - uᵢ∂ᵢpₙₕₛ
```

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size = (1, 1, 4), extent = (1, 1, 1));

julia> model = NonhydrostaticModel(; grid);

julia> using Oceanostics.TKEBudgetTerms: KineticEnergyTendency

julia> ke_tendency = KineticEnergyTendency(model)
KernelFunctionOperation at (Center, Center, Center)
├── grid: 1×1×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×1×3 halo
├── kernel_function: uᵢGᵢᶜᶜᶜ (generic function with 1 method)
└── arguments: ("Centered(order=2)", "Nothing", "Nothing", "Nothing", "FluxBoundaryCondition: Nothing", "FluxBoundaryCondition: Nothing", "FluxBoundaryCondition: Nothing", "Nothing", "(velocities=(u=ZeroField{Int64}, v=ZeroField{Int64}, w=ZeroField{Int64}), tracers=NamedTuple())", "(u=1×1×4 Field{Face, Center, Center} on RectilinearGrid on CPU, v=1×1×4 Field{Center, Face, Center} on RectilinearGrid on CPU, w=1×1×5 Field{Center, Center, Face} on RectilinearGrid on CPU)", "NamedTuple()", "NamedTuple()", "Nothing", "Nothing", "Clock{Float64, Float64}(time=0 seconds, iteration=0, last_Δt=Inf days)", "(u=zeroforcing (generic function with 1 method), v=zeroforcing (generic function with 1 method), w=zeroforcing (generic function with 1 method))")
```
