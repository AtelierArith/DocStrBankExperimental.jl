```
Integral(field::AbstractField; dims=:, condition=nothing, mask=0)
```

`field`の空間積分を`dims`にわたって表す`Reduction`を返します。

`condition`および`mask`キーワード引数を使用した情報と例については、[`ConditionalOperation`](@ref Oceananigans.AbstractOperations.ConditionalOperation)を参照してください。

# 例

領域$(x, y, z) ∈ [0, 1] × [0, 1] × [0, 1]$にわたる$f(x, y, z) = x y z$の積分を計算します。解析的な答えは$∭ x y z \, dx \, dy \, dz = 1/8$です。

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(8, 8, 8), x=(0, 1), y=(0, 1), z=(0, 1));

julia> f = CenterField(grid);

julia> set!(f, (x, y, z) -> x * y * z)
8×8×8 Field{Center, Center, Center} on RectilinearGrid on CPU
├── grid: 8×8×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 3×3×3 halo
├── boundary conditions: FieldBoundaryConditions
│   └── west: Periodic, east: Periodic, south: Periodic, north: Periodic, bottom: ZeroFlux, top: ZeroFlux, immersed: ZeroFlux
└── data: 14×14×14 OffsetArray(::Array{Float64, 3}, -2:11, -2:11, -2:11) with eltype Float64 with indices -2:11×-2:11×-2:11
    └── max=0.823975, min=0.000244141, mean=0.125

julia> ∫f = Integral(f)
Integral of BinaryOperation at (Center, Center, Center) over dims (1, 2, 3)
└── operand: BinaryOperation at (Center, Center, Center)
    └── grid: 8×8×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 3×3×3 halo

julia> ∫f = Field(Integral(f));

julia> compute!(∫f);

julia> ∫f[1, 1, 1]
0.125
```
