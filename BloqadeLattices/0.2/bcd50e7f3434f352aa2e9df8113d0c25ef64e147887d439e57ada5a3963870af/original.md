```
deleteat!(sites::AtomList, indices...)
```

Deletes an atom from `sites` via its index/indices.

When `sites` is displayed after deletion the atoms will be renumbered to maintain a proper integer sequence, e.g. given a sequence of atoms numbered "1,2,3,4", if atom 3 is deleted then the new ordering will be "1,2,3".

```jldoctest; setup=:(using BloqadeLattices)
julia> sites = generate_sites(SquareLattice(), 2, 2, scale=6.7)
4-element AtomList{2, Float64}:
 (0.0, 0.0)
 (6.7, 0.0)
 (0.0, 6.7)
 (6.7, 6.7)

julia> deleteat!(sites, 2, 3)
2-element AtomList{2, Float64}:
 (0.0, 0.0)
 (6.7, 6.7)
```
