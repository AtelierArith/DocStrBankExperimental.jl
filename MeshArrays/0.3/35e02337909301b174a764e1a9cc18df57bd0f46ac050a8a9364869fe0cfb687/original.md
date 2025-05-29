```
Tiles(γ::gcmgrid,ni::Int,nj::Int)
```

Define sudomain `tiles` of size `ni,nj`. Each tile is defined by a `Dict` where `tile,face,i,j` correspond to tile ID, face ID, index ranges.

```jldoctest; output = false
using MeshArrays
γ=GridSpec("LatLonCap",MeshArrays.GRID_LLC90)
τ=Tiles(γ,30,30)

isa(τ[1],NamedTuple)

# output

true
```
