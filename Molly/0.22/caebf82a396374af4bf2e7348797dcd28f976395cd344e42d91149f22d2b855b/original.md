```
CellListMapNeighborFinder(; eligible, dist_cutoff, special, n_steps, x0, unit_cell)
```

Find close atoms by distance using a cell list algorithm from CellListMap.jl.

This is the recommended neighbor finder on CPU. `x0` and `unit_cell` are optional initial coordinates and system unit cell that improve the first approximation of the cell list structure. Can not be used if one or more dimensions has infinite boundaries.

### Example

```julia-repl
julia> coords
15954-element Vector{SVector{3, Quantity{Float64, 𝐋, Unitful.FreeUnits{(nm,), 𝐋, nothing}}}}:
 [2.5193063341012127 nm, 3.907448346081021 nm, 4.694954671434135 nm]
 [2.4173958848835233 nm, 3.916034913604175 nm, 4.699661024574953 nm]
 ⋮
 [1.818842280373283 nm, 5.592152965227421 nm, 4.992100424805031 nm]
 [1.7261366568663976 nm, 5.610326185704369 nm, 5.084523386833478 nm]

julia> boundary
CubicBoundary{Quantity{Float64, 𝐋, Unitful.FreeUnits{(nm,), 𝐋, nothing}}}(Quantity{Float64, 𝐋, Unitful.FreeUnits{(nm,), 𝐋, nothing}}[5.676 nm, 5.6627 nm, 6.2963 nm])

julia> neighbor_finder = CellListMapNeighborFinder(
           eligible=s.neighbor_finder.eligible, dist_cutoff=1.2u"nm",
           special=s.neighbor_finder.special, n_steps=10,
           x0=coords, unit_cell=boundary,
       )
CellListMapNeighborFinder{Quantity{Float64, 𝐋, Unitful.FreeUnits{(nm,), 𝐋, nothing}}, 3, Float64}
  Size of eligible matrix = (15954, 15954)
  n_steps = 10
  dist_cutoff = 1.2 nm

```
