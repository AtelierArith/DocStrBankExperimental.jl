```
Tiles(τ::Array{Dict},x::MeshArray)
```

Return an `Array` of tiles which cover `x` according to tile partition `τ`.

```jldoctest; output = false
using MeshArrays
γ=GridSpec("LatLonCap",MeshArrays.GRID_LLC90)
d=γ.read(γ.path*"Depth.data",MeshArray(γ,γ.ioPrec))
τ=Tiles(γ,30,30)
td=Tiles(τ,d)

D=similar(d)
Tiles!(τ,td,D)

isa(td[1],Array)

# output

true
```
