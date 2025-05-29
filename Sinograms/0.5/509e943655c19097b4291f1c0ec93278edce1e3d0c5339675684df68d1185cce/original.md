```
CtFanFlat( ; ns nt ds dt offset_s offset_t
    na orbit orbit_start
    dsd = 4ns * ds, dod = ns * ds)
CtFanFlat(:short ; ...)
```

Constructor with named keywords. See `?CtGeom` for documentation.

  * Use `:short` argument to specify a short scan, in which case `na` will be scaled down proportionally as well.

```jldoctest
julia> CtFanFlat()
CtFanFlat{Float32, Float32, CtSourceCircle} :
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
