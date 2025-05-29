```
SinoFanArc( ; nb d offset na orbit orbit_start
    source_offset, dsd = 4 * nb * d, dod = nb * d)
SinoFanArc(:short ; ...)
```

Constructor with named keywords. See `?SinoGeom` for documentation.

  * `d`, `source_offset`, `dsd`, `dod` must all have the same units.
  * Use `:short` argument to specify a short scan, in which case `na` will be scaled down proportionally as well.

```jldoctest
julia> SinoFanArc()
SinoFanArc{Float32, Float32} :
 nb::Int64 128
 d::Float32 1.0
 offset::Float32 0.0
 na::Int64 200
 orbit::Float32 360.0
 orbit_start::Float32 0.0
 source_offset::Float32 0.0
 dsd::Float32 512.0
 dod::Float32 128.0
```
