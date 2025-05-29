```
Partition(; x = 1, y = 1, z = 1)
```

Return `Partition` representing the division of a domain in the `x` (first), `y` (second) and `z` (third) dimension

# Keyword arguments:

  * `x`: partitioning of the first dimension
  * `y`: partitioning of the second dimension
  * `z`: partitioning of the third dimension

if supplied as positional arguments `x` will be the first argument, `y` the second and `z` the third

`x`, `y` and `z` can be:

  * `x::Int`: allocate `x` processors to the first dimension
  * `Equal()`: divide the domain in `x` equally among the remaining processes (not supported for multiple directions)
  * `Fractional(ϵ₁, ϵ₂, ..., ϵₙ):` divide the domain unequally among `N` processes. The total work is `W = sum(ϵᵢ)`,                                and each process is then allocated `ϵᵢ / W` of the domain.
  * `Sizes(n₁, n₂, ..., nₙ)`: divide the domain unequally. The total work is `W = sum(nᵢ)`,                           and each process is then allocated `nᵢ`.

# Examples:

```jldoctest
julia> using Oceananigans; using Oceananigans.DistributedComputations

julia> Partition(1, 4)
Partition across 4 = 1×4×1 ranks:
└── y: 4

julia> Partition(x = Fractional(1, 2, 3, 4))
Partition across 4 = 4×1×1 ranks:
└── x: Fractional(0.1, 0.2, 0.3, 0.4)

```
