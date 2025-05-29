```
setboundaries(lat, boundaries...[; checkboundaries=true, rmdup=false])
```

Set the boundary conditions for the lattice `lat`.

## Arguments

  * `lat`: The lattice.
  * `boundaries`: The boundary conditions. It can be a single `Boundary` or a `Tuple` of `Boundary` objects.

## Keyword arguments

  * `checkboundaries`: If `true`, check if the boundary conditions overlap within the lattice sites.
  * `rmdup`: If `true`, remove duplicate sites from the lattice.

## Example

```jldoctest
julia> using LatticeModels

julia> l = SquareLattice(4, 4);

julia> l2 = setboundaries(l, [4, 0] => true, [0, 4] => pi);

julia> l2.boundaries
Boundary conditions (depth = 1):
  Bravais[4, 0] → periodic
  Bravais[0, 4] → twist θ = 3.14
```
