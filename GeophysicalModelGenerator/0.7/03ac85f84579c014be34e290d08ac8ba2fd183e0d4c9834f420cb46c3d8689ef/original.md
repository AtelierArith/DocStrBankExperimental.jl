Structure that holds profile data (interpolated/projected on the profile)

```
struct ProfileData
    vertical        ::  Bool # vertical:true, horizontal:false
    start_lonlat    ::  Union{Nothing,Tuple{Float64,Float64}}
    end_lonlat      ::  Union{Nothing,Tuple{Float64,Float64}}
    depth           ::  Union{Nothing,Float64}
    VolData         ::  GeophysicalModelGenerator.GeoData
    SurfData        ::  Union{Nothing, NamedTuple}
    PointData       ::  Union{Nothing, NamedTuple}
end

Structure to store cross section data
```
