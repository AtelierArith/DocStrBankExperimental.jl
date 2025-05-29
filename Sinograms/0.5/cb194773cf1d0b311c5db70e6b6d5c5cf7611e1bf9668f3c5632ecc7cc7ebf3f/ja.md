```
CtPar( ; ns nt ds dt offset_s offset_t na orbit orbit_start)
```

名前付きキーワードを持つコンストラクタ。ドキュメントについては `?CtGeom` を参照してください。

```jldoctest
julia> CtPar()
CtPar{Float32, Float32, CtSourceCircle} :
 ns::Int64 128
 nt::Int64 64
 ds::Float32 1.0
 dt::Float32 1.0
 offset_s::Float32 0.0
 offset_t::Float32 0.0
 na::Int64 60
 orbit::Float32 180.0
 orbit_start::Float32 0.0
 src::CtSourceCircle CtSourceCircle()
```
