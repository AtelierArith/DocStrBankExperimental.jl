```
CtFanArc( ; ns nt ds dt offset_s offset_t
    na orbit orbit_start
    dsd = 4ns * ds, dod = ns * ds)
CtFanArc(:short ; ...)
```

名前付きキーワードを持つコンストラクタ。ドキュメントについては `?CtGeom` を参照してください。

  * `:short` 引数を使用して短いスキャンを指定します。この場合、`na` は比例的に縮小されます。

```jldoctest
julia> CtFanArc()
CtFanArc{Float32, Float32, CtSourceCircle} :
 ns::Int64 128
 nt::Int64 64
 ds::Float32 1.0
 dt::Float32 1.0
 offset_s::Float32 0.0
 offset_t::Float32 0.0
 na::Int64 64
 orbit::Float32 360.0
 orbit_start::Float32 0.0
 source_offset::Float32 0.0
 dsd::Float32 512.0
 dod::Float32 128.0
 src::CtSourceCircle CtSourceCircle()
```
