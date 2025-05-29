```julia
TracerVarianceTendency(model, tracer_name; location)

```

トレーサー分散傾向を計算する `KernelFunctionOperation` を返します：

```
TEND = 2 c ∂ₜc
```

ここで `c` はトレーサーであり、`∂ₜc` はトレーサー傾向（Oceananigans のトレーサー傾向カーネルを使用して計算されます）です。

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
