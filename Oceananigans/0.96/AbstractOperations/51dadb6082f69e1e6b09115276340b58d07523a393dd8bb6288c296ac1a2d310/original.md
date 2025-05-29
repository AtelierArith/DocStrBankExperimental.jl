```
CumulativeIntegral(field::AbstractField; dims, reverse=false, condition=nothing, mask=0)
```

Return an `Accumulation` representing the cumulative spatial integral of `field` over `dims`.

See [`ConditionalOperation`](@ref Oceananigans.AbstractOperations.ConditionalOperation) for information and examples using `condition` and `mask` kwargs.

# Example

Compute the cumulative integral of $f(z) = z$ over z ∈ [0, 1].

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=8, z=(0, 1), topology=(Flat, Flat, Bounded));

julia> c = CenterField(grid);

julia> set!(c, z -> z)
1×1×8 Field{Center, Center, Center} on RectilinearGrid on CPU
├── grid: 1×1×8 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── boundary conditions: FieldBoundaryConditions
│   └── west: Nothing, east: Nothing, south: Nothing, north: Nothing, bottom: ZeroFlux, top: ZeroFlux, immersed: ZeroFlux
└── data: 1×1×14 OffsetArray(::Array{Float64, 3}, 1:1, 1:1, -2:11) with eltype Float64 with indices 1:1×1:1×-2:11
    └── max=0.9375, min=0.0625, mean=0.5

julia> C_op = CumulativeIntegral(c, dims=3)
CumulativeIntegral of BinaryOperation at (Center, Center, Center) over dims 3
└── operand: BinaryOperation at (Center, Center, Center)
    └── grid: 1×1×8 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo

julia> C = compute!(Field(C_op))
1×1×8 Field{Center, Center, Center} on RectilinearGrid on CPU
├── data: OffsetArrays.OffsetArray{Float64, 3, Array{Float64, 3}}, size: (1, 1, 8)
├── grid: 1×1×8 RectilinearGrid{Float64, Flat, Flat, Bounded} on CPU with 0×0×3 halo
├── operand: CumulativeIntegral of BinaryOperation at (Center, Center, Center) over dims 3
├── status: time=0.0
└── data: 1×1×14 OffsetArray(::Array{Float64, 3}, 1:1, 1:1, -2:11) with eltype Float64 with indices 1:1×1:1×-2:11
    └── max=0.5, min=0.0078125, mean=0.199219

julia> C[1, 1, 8]
0.5
```
