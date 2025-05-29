```
generate_sites_in_region(lattice::AbstractLattice{D}, region::AbstractRegion{D})
```

Generates sites from the `lattice` that are present in the `region`.

```jldoctest; setup=:(using BloqadeLattices)
julia> generate_sites_in_region(ChainLattice(), Parallelepiped(4.0))
4-element Vector{Tuple{Float64}}:
 (0.0,)
 (1.0,)
 (2.0,)
 (3.0,)

julia> bounds = zeros(2,2)
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0

julia> bounds[:,1] .= (0.0, 2.0); bounds[:,2] .= (2.0, 0.0);

julia> generate_sites_in_region(SquareLattice(), Parallelepiped(bounds))
4-element Vector{Tuple{Float64, Float64}}:
 (0.0, 0.0)
 (1.0, 0.0)
 (0.0, 1.0)
 (1.0, 1.0)
```
