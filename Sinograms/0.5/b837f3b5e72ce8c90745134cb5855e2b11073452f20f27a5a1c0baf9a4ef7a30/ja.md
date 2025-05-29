```
SinoFanArc(Val(:ge1) ; kwargs...)
```

GE LightspeedシステムCTジオメトリ。

# オプション

  * `unit::RealU = 1` または `1mm` を使用
  * `nb::Int = 888` # 検出器チャネルの数
  * `d::RealU = 1.0239` チャネル間隔
  * `offset::Real = 1.25` "クォーターディテクタ"オフセット用
  * `na::Int = 984` # 角度の数
  * `orbit::Union{Symbol,Real} = 360` 短いスキャンには `:short` を使用
  * `dsd::RealU = 949.075`
  * `dod::RealU = 408.075`

# 出力

  * `SinoFanArc`

これらの数値はIEEE T-MI 2006年10月、p.1272-1283に掲載されています wang:06:pwl。

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
