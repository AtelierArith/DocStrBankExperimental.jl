```
Data_interp = interpolate_datafields(V::AbstractGeneralGrid, Lon, Lat, Depth)
```

Interpolates a data field `V` on a grid defined by `Lon,Lat,Depth`

# Example

```julia
julia> x        =   0:2:10
julia> y        =   -5:5
julia> z        =   -10:2:2
julia> X,Y,Z    =   xyz_grid(x, y, z);
julia> Data     =   Z
julia> Data_set1=   CartData(X,Y,Z, (FakeData=Data,Data2=Data.+1.))
CartData
    size    : (6, 11, 7)
    x       ϵ [ 0.0 km : 10.0 km]
    y       ϵ [ -5.0 km : 5.0 km]
    z       ϵ [ -10.0 km : 2.0 km]
    fields  : (:FakeData, :Data2)
  attributes: ["note"]

julia> X,Y,Z    =   xyz_grid(0:4:10, -1:.1:1, -5:.1:1 );
julia> Data_set2= interpolate_datafields(Data_set1, X,Y,Z)
```
