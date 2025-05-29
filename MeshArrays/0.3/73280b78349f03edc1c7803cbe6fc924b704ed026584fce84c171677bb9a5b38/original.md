```
GridSpec(category="PeriodicDomain",path=tempname(); np=nothing, ID=:unknown)
```

  * Select one of the pre-defined grids either by ID (keyword) or by category.
  * Return the corresponding `gcmgrid` specification, including the path where grid files can be accessed (`path`).

1. selection by `ID`

  * `:LLC90`
  * `:CS32`
  * `:LLC270`
  * `:onedegree`
  * `:default`

Example:

```
using MeshArrays
g = GridSpec(ID=:LLC90)
```

note : the path to these fully supported grids are handled internally in `MeshArrays.jl`.

2. by `category` and `path`

  * `"PeriodicDomain"`
  * `"PeriodicChannel"`
  * `"CubeSphere"`
  * `"LatLonCap"``

Examples:

```jldoctest; output = false
using MeshArrays
g = GridSpec()
g = GridSpec("PeriodicChannel",MeshArrays.GRID_LL360)
g = GridSpec("CubeSphere",MeshArrays.GRID_CS32)
g = GridSpec("LatLonCap",MeshArrays.GRID_LLC90)
isa(g,gcmgrid)

# output

true
```

3. by `category` and `path` with the `np` argument

  * `np` is the number of grid points in x or y for the `LatLonCap` and `CubeSphere` tiles.

`np` defaults to 90 for `LatLonCap` and 32 for `CubeSphere`, and so must be included to access the LLC270 grid with the category argument.

Examples:

```jldoctest; output = false
using MeshArrays
g = GridSpec("LatLonCap",MeshArrays.GRID_LLC90,np=90)
g = GridSpec("LatLonCap",MeshArrays.GRID_LLC270,np=270)
g = GridSpec("CubeSphere",MeshArrays.GRID_CS32,np=32)
isa(g,gcmgrid)

# output

true
```
