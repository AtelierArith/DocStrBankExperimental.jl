```
Tiles(γ::gcmgrid,ni::Int,nj::Int)
```

サイズ `ni,nj` のサブドメイン `tiles` を定義します。各タイルは、`tile,face,i,j` がタイルID、フェイスID、インデックス範囲に対応する `Dict` によって定義されます。

```jldoctest; output = false
using MeshArrays
γ=GridSpec("LatLonCap",MeshArrays.GRID_LLC90)
τ=Tiles(γ,30,30)

isa(τ[1],NamedTuple)

# output

true
```
