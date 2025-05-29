```julia
PotentialEnergy(model; location, geopotential_height)

```

各グリッド `location` における単位体積あたりの `PotentialEnergy` を計算する `KernelFunctionOperation` を返します。

$$
Eₚ = \frac{gρ}{ρ₀}z = -bz
$$

`PotentialEnergy` は `BuoyancyTracer` と `SeawaterBuoyancy` の両方に対して定義されています。利用可能なオプションについての詳細は、関連する Oceananigans.jl ドキュメントの [buoyancy models](https://clima.github.io/OceananigansDocumentation/dev/model_setup/buoyancy_and_equation_of_state/) を参照してください。

オプションのキーワード引数 `geopotential_height` は、`BoussinesqEquationOfState` を使用する際に、現地密度ではなく `geopotential_height` に基づいた潜在密度で `Eₚ` を計算したい場合にのみ使用されます。

# 例

`BuoyancyTracer` 浮力モデルを使用した場合

```jldoctest
julia> using Oceananigans

julia> using Oceanostics.PotentialEnergyEquationTerms: PotentialEnergy

julia> grid = RectilinearGrid(size=100, z=(-1000, 0), topology=(Flat, Flat, Bounded))
1×1×100 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── Flat x
├── Flat y
└── Bounded  z ∈ [-1000.0, 0.0] regularly spaced with Δz=10.0

julia> model = NonhydrostaticModel(; grid, buoyancy=BuoyancyTracer(), tracers=(:b,))
NonhydrostaticModel{CPU, RectilinearGrid}(time = 0 seconds, iteration = 0)
├── grid: 1×1×100 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── timestepper: RungeKutta3TimeStepper
├── advection scheme: Centered(order=2)
├── tracers: b
├── closure: Nothing
├── buoyancy: BuoyancyTracer with ĝ = NegativeZDirection()
└── coriolis: Nothing

julia> PotentialEnergy(model)
KernelFunctionOperation at (Center, Center, Center)
├── grid: 1×1×100 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── kernel_function: minus_bz_ccc (generic function with 3 methods)
└── arguments: ("1×1×100 Field{Center, Center, Center} on RectilinearGrid on CPU",)
```

`PotentialEnergy` のデフォルトの動作は、状態方程式が `BoussinesqEquationOfState` の場合、計算に *現地密度* を使用します。

```jldoctest
julia> using Oceananigans, SeawaterPolynomials.TEOS10

julia> using Oceanostics.PotentialEnergyEquationTerms: PotentialEnergy

julia> grid = RectilinearGrid(size=100, z=(-1000, 0), topology=(Flat, Flat, Bounded))
1×1×100 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── Flat x
├── Flat y
└── Bounded  z ∈ [-1000.0, 0.0] regularly spaced with Δz=10.0

julia> tracers = (:T, :S)
(:T, :S)

julia> eos = TEOS10EquationOfState()
BoussinesqEquationOfState{Float64}:
    ├── seawater_polynomial: TEOS10SeawaterPolynomial{Float64}
    └── reference_density: 1020.0

julia> buoyancy = SeawaterBuoyancy(equation_of_state=eos)
SeawaterBuoyancy{Float64}:
├── gravitational_acceleration: 9.80665
└── equation_of_state: BoussinesqEquationOfState{Float64}

julia> model = NonhydrostaticModel(; grid, buoyancy, tracers)
NonhydrostaticModel{CPU, RectilinearGrid}(time = 0 seconds, iteration = 0)
├── grid: 1×1×100 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── timestepper: RungeKutta3TimeStepper
├── advection scheme: Centered(order=2)
├── tracers: (T, S)
├── closure: Nothing
├── buoyancy: SeawaterBuoyancy with g=9.80665 and BoussinesqEquationOfState{Float64} with ĝ = NegativeZDirection()
└── coriolis: Nothing

julia> PotentialEnergy(model)
KernelFunctionOperation at (Center, Center, Center)
├── grid: 1×1×100 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── kernel_function: minus_bz_ccc (generic function with 3 methods)
└── arguments: ("KernelFunctionOperation at (Center, Center, Center)", "(g=9.80665, ρ₀=1020.0)")
```

参照密度を使用するには、キーワード引数 `geopotential_height` に定数値を設定し、これを関数に渡します。例えば、

```jldoctest
julia> using Oceananigans, SeawaterPolynomials.TEOS10;

julia> using Oceanostics.PotentialEnergyEquationTerms: PotentialEnergy;

julia> grid = RectilinearGrid(size=100, z=(-1000, 0), topology=(Flat, Flat, Bounded));

julia> tracers = (:T, :S);

julia> eos = TEOS10EquationOfState();

julia> buoyancy = SeawaterBuoyancy(equation_of_state=eos);

julia> model = NonhydrostaticModel(; grid, buoyancy, tracers);

julia> geopotential_height = 0; # 密度変数は σ₀ になります

julia> PotentialEnergy(model)
KernelFunctionOperation at (Center, Center, Center)
├── grid: 1×1×100 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── kernel_function: minus_bz_ccc (generic function with 3 methods)
└── arguments: ("KernelFunctionOperation at (Center, Center, Center)", "(g=9.80665, ρ₀=1020.0)")
```
