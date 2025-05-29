プロファイルデータを保持する構造体（プロファイル上で補間/予測された）

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

断面データを格納する構造体
```
