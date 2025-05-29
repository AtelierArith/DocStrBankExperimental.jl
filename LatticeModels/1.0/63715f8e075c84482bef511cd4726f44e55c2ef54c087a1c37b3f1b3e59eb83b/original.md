```
GenericLattice{SiteT}
```

A generic lattice of `SiteT` sites.

## Example

```jldoctest
julia> using LatticeModels

julia> l = GenericLattice{2}()
0-site GenericLattice{GenericSite{2}} in 2D space

julia> push!(l, GenericSite(0, 0))  # Add a site at (0, 0)
1-site GenericLattice{GenericSite{2}} in 2D space:
  Site at [0.0, 0.0]

julia> push!(l, (0, 1))             # Add a site at (0, 1)
2-site GenericLattice{GenericSite{2}} in 2D space:
  Site at [0.0, 0.0]
  Site at [0.0, 1.0]

julia> push!(l, [1, 0])             # Add a site at (1, 0)
3-site GenericLattice{GenericSite{2}} in 2D space:
  Site at [0.0, 0.0]
  Site at [0.0, 1.0]
  Site at [1.0, 0.0]

julia> l[2]
2-dim GenericSite{2} at [0.0, 1.0]
```
