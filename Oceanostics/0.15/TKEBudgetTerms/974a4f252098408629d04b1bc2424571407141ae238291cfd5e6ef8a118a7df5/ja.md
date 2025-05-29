```julia
PressureRedistributionTerm(
    model;
    velocities,
    pressure,
    location
)

```

圧力再分配項を計算する `KernelFunctionOperation` を返します：

```
PR = uᵢ∂ᵢp
```

ここで `p` は圧力です。デフォルトでは `p` は総圧力（非静水圧 + 静水圧）と見なされます：

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

`velocities` と `pressure` のキーワードを渡すことで、より具体的な計算を行うこともできます。以下の例は、圧力再分配項への非静水圧の寄与の計算を示しています：

```jldoctest ∇u⃗p_example
julia> ∇u⃗pNHS = PressureRedistributionTerm(model, pressure=model.pressures.pNHS)
KernelFunctionOperation at (Center, Center, Center)
├── grid: 1×1×4 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 1×1×3 halo
├── kernel_function: uᵢ∂ᵢpᶜᶜᶜ (generic function with 1 method)
└── arguments: ("(u=1×1×4 Field{Face, Center, Center} on RectilinearGrid on CPU, v=1×1×4 Field{Center, Face, Center} on RectilinearGrid on CPU, w=1×1×5 Field{Center, Center, Face} on RectilinearGrid on CPU)", "1×1×4 Field{Center, Center, Center} on RectilinearGrid on CPU")
```
