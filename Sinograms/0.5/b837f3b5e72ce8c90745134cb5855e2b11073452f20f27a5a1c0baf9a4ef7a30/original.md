```
SinoFanArc(Val(:ge1) ; kwargs...)
```

GE Lightspeed system CT geometry.

# option

  * `unit::RealU = 1` or use `1mm`
  * `nb::Int = 888` # of detector channels
  * `d::RealU = 1.0239` channel spacing
  * `offset::Real = 1.25` for "quarter-detector" offset
  * `na::Int = 984` # of angles
  * `orbit::Union{Symbol,Real} = 360` use `:short` for short scan
  * `dsd::RealU = 949.075`
  * `dod::RealU = 408.075`

# out

  * `SinoFanArc`

These numbers are published in IEEE T-MI Oct. 2006, p.1272-1283 wang:06:pwl.

```jldoctest
julia> SinoFanArc(Val(:ge1))
SinoFanArc{Float32, Float32} :
 nb::Int64 888
 d::Float32 1.0239
 offset::Float32 1.25
 na::Int64 984
 orbit::Float32 360.0
 orbit_start::Float32 0.0
 source_offset::Float32 0.0
 dsd::Float32 949.075
 dod::Float32 408.075
```
