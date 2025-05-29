```julia
ErtelPotentialVorticity(model; tracer, location)

```

`model`のためのErtelポテンシャル渦度を計算します。コリオリ回転の特性は`model.coriolis`から取得されます。Ertelポテンシャル渦度は次のように定義されます。

```
EPV = ωₜₒₜ ⋅ ∇b
```

ここで、ωₜₒₜは全体（相対 + 惑星）渦度ベクトル、`b`は浮力、∇は勾配演算子です。

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

EPVの値は、内部と境界の両方で正しく計算されることに注意してください。内部および上部境界では、EPV = f×N² = 10⁻¹⁰であり、下部境界では∂b/∂zがゼロであるため、EPV = 0です。
