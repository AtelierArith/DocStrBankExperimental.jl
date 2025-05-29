```
setnnbonds(lat, args...; overwrite=false)
```

Adds the nearest neighbor bonds `args` to the lattice `lat`. If `overwrite` is `true`, the default nearest neighbor bonds are replaced by `args`. Otherwise, the new bonds are merged with the default.

Each `args` can be a bonds type or a distance-bonds pair.

## Example

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(3, 3);

julia> lat2 = setnnbonds(lat, SiteDistance(0 .. 1), SiteDistance(1 .. 2));

julia> lat2.nnbonds
Nearest neighbor hoppings:
  #1 =>
    SiteDistance(0 .. 1)
  #2 =>
    SiteDistance(1 .. 2)
```
