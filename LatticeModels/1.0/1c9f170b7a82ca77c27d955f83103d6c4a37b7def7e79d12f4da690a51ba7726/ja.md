```
NearestNeighbor(lat[, N=1])
```

格子 `lat` の順序 `N` の最近接隣接結合を返します。

## 例

```jldoctest
julia> using LatticeModels

julia> lat = HoneycombLattice(5, 5);

julia> NearestNeighbor(lat)
BravaisSiteMapping with 3 translations:
  1 => 2, [0, -1]
  1 => 2, [-1, 0]
  1 => 2, [0, 0]
 on 50-site HoneycombLattice in 2D space

julia> lat = SquareLattice(3, 3, 3, 3);

julia> NearestNeighbor(lat, 4)
BravaisSiteMapping with 12 translations:
  Bravais[1, -1, -1, -1]
  Bravais[1, 1, -1, -1]
  Bravais[1, -1, 1, -1]
  Bravais[1, 1, 1, -1]
  Bravais[2, 0, 0, 0]
  Bravais[0, 2, 0, 0]
  Bravais[0, 0, 2, 0]
  Bravais[1, -1, -1, 1]
  Bravais[1, 1, -1, 1]
   ⋮
 on 81-site SquareLattice in 4D space
```
