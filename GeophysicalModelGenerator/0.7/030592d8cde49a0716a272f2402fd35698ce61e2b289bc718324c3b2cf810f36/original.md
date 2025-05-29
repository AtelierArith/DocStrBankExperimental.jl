```
save_GMG(filename::String, data::Union{GeoData, CartDat, UTMData}; dir=pwd())
```

Saves the dataset `data` to a JLD2 `file` (name without extension) in the directory `dir`

# Example

```julia
julia> Lon3D,Lat3D,Depth3D = lonlatdepth_grid(1.0:3:10.0, 11.0:4:20.0, (-20:5:-10)*km);
julia> Data_set    =   GeophysicalModelGenerator.GeoData(Lon3D,Lat3D,Depth3D,(DataFieldName=Depth3D,))   
julia> save_GMG("test",Data_set)
```
