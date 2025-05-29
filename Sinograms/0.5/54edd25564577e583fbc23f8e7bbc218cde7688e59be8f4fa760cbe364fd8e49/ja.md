```
CtFanArc(::Val{:ge1} ; kwargs...)
```

GE LightspeedシステムCTジオメトリ。

# オプション

  * `unit::RealU = 1` または `1mm` を使用
  * (see `CtFanArc`)

# 出力

  * `CtFanArc`

これらの数値はIEEE T-MI 2006年10月、p.1272-1283に掲載されています wang:06:pwl。

```jldoctest
julia> CtFanArc(Val(:ge1))
CtFanArc{Float64, Float32, CtSourceCircle} :
 ns::Int64 888
 nt::Int64 64
 ds::Float64 1.0239
 dt::Float64 1.0964
 offset_s::Float32 1.25
 offset_t::Float32 0.0
 na::Int64 984
 orbit::Float32 360.0
 orbit_start::Float32 0.0
 source_offset::Float64 0.0
 dsd::Float64 949.075
 dod::Float64 408.075
 src::CtSourceCircle CtSourceCircle()
```
