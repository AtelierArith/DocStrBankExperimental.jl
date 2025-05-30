```
GridLoad(γ=GridSpec(); ID=:default, option=:minimal)
```

  * Return a `NamedTuple` of grid variables read from files located in `γ.path` (see `?GridSpec`).
  * option : 

      * (default) option=:minimal means that only grid cell center positions (XC, YC) are loaded.
      * option=:full provides a complete set of 2D grid variables.
      * option=:full provides a complete set of 2D & 3D grid variables.

Based on the MITgcm naming convention, grid variables are:

  * XC, XG, YC, YG, AngleCS, AngleSN, hFacC, hFacS, hFacW, Depth.
  * RAC, RAW, RAS, RAZ, DXC, DXG, DYC, DYG.
  * DRC, DRF, RC, RF (one-dimensional)

MITgcm documentation : 

https://mitgcm.readthedocs.io/en/latest/algorithm/algorithm.html#spatial-discretization-of-the-dynamical-equations

```jldoctest; output = false
using MeshArrays
γ = GridSpec(ID=:LLC90)
Γ = GridLoad(γ;option="full")

isa(Γ.XC,MeshArray)

# output

true
```
