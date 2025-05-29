```
DatasetcountMap = countmap(DataSet::GeoData,field::String,stepslon::Int64,stepslat::Int64)
```

Takes a 2D GeoData struct and counts entries of `field` per predefined control area. `field` should only consist of 1.0s and 0.0s. The control area is defined by `steplon` and `steplat`. `steplon` is the number of control areas in longitude direction and `steplat` the number of control areas in latitude direction. The counts per control area are normalized by the highest count.

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
