```
GridLoadVar(nam::String,γ::gcmgrid)
```

Return a grid variable read from files located in `γ.path` (see `?GridSpec`, `?GridLoad`).

Based on the MITgcm naming convention, grid variables are:

  * XC, XG, YC, YG, AngleCS, AngleSN, hFacC, hFacS, hFacW, Depth.
  * RAC, RAW, RAS, RAZ, DXC, DXG, DYC, DYG.
  * DRC, DRF, RC, RF (one-dimensional)

MITgcm documentation : 

https://mitgcm.readthedocs.io/en/latest/algorithm/algorithm.html#spatial-discretization-of-the-dynamical-equations

```jldoctest; output = false
using MeshArrays

γ = GridSpec("CubeSphere",MeshArrays.GRID_CS32)
XC = GridLoadVar("XC",γ)

isa(XC,MeshArray)

# output

true
```
