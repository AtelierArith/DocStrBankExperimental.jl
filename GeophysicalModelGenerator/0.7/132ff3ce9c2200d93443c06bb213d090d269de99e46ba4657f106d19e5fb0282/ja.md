```
DatasetcountMap = countmap(DataSet::GeoData,field::String,stepslon::Int64,stepslat::Int64)
```

2D GeoData 構造体を取り込み、事前に定義された制御領域ごとに `field` のエントリをカウントします。`field` は 1.0 と 0.0 のみで構成されるべきです。制御領域は `steplon` と `steplat` によって定義されます。`steplon` は経度方向の制御領域の数で、`steplat` は緯度方向の制御領域の数です。制御領域ごとのカウントは、最高カウントで正規化されます。

```julia
julia> Data_Faults         = GeoData(Lon3D,Lat3D,Faults,(Faults=Faults,))
GeoData 
    size      : (375, 208, 1)
    lon       ϵ [ -9.932408319802885 : 34.93985125012068]
    lat       ϵ [ 35.086096468211394 : 59.919210145128545]
    depth     ϵ [ 0.0 : 1.0]
    fields    : (:Faults,)

julia> steplon  = 125
julia> steplat  = 70
julia> countmap = countmap(Data_Faults,"Faults",steplon,steplat)

GeoData 
    size      : (124, 69, 1)
    lon       ϵ [ -9.751471789279 : 34.75891471959677]
    lat       ϵ [ 35.26604656731949 : 59.73926004602028]
    depth     ϵ [ 0.0 : 1.0]
    fields    : (:countmap,)
```

julia
