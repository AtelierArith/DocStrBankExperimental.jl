```
GeoData(lon::Any, lat:Any, depth::GeoUnit, fields::NamedTuple)
```

Data structure that holds one or several fields with longitude, latitude and depth information.

  * `depth` can have units of meter, kilometer or be unitless; it will be converted to km.
  * `fields` should ideally be a NamedTuple which allows you to specify the names of each of the fields.
  * In case you only pass one array we will convert it to a NamedTuple with default name.
  * A single field should be added as `(DataFieldName=Data,)` (don't forget the comma at the end).
  * Multiple fields  can be added as well. `lon`,`lat`,`depth` should all have the same size as each of the `fields`.
  * In case you want to display a vector field in paraview, add it as a tuple: `(Velocity=(Veast,Vnorth,Vup), Veast=Veast, Vnorth=Vnorth, Vup=Vup)`; we automatically apply a vector transformation when transforming this to a `ParaviewData` structure from which we generate Paraview output. As this changes the magnitude of the arrows, you will no longer see the `[Veast,Vnorth,Vup]` components in Paraview which is why it is a good ideas to store them as separate Fields.
  * Yet, there is one exception: if the name of the 3-component field is `colors`, we do not apply this vector transformation as this field is regarded to contain RGB colors.
  * `Lat`,`Lon`,`Depth` should have the same size as the `Data` array. The ordering of the arrays is important. If they are 3D arrays, as in the example below, we assume that the first dimension corresponds to `lon`, second dimension to `lat` and third dimension to `depth` (which should be in km). See below for an example.

# Example

```julia-repl
julia> Lat         =   1.0:3:10.0;
julia> Lon         =   11.0:4:20.0;
julia> Depth       =   (-20:5:-10)*km;
julia> Lon3D,Lat3D,Depth3D = lonlatdepth_grid(Lon, Lat, Depth);
julia> Lon3D
3×4×3 Array{Float64, 3}:
[:, :, 1] =
 11.0  11.0  11.0  11.0
 15.0  15.0  15.0  15.0
 19.0  19.0  19.0  19.0

[:, :, 2] =
 11.0  11.0  11.0  11.0
 15.0  15.0  15.0  15.0
 19.0  19.0  19.0  19.0

[:, :, 3] =
 11.0  11.0  11.0  11.0
 15.0  15.0  15.0  15.0
 19.0  19.0  19.0  19.0
julia> Lat3D
 3×4×3 Array{Float64, 3}:
 [:, :, 1] =
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0

 [:, :, 2] =
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0

 [:, :, 3] =
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0
  1.0  4.0  7.0  10.0
julia> Depth3D
  3×4×3 Array{Unitful.Quantity{Float64, 𝐋, Unitful.FreeUnits{(km,), 𝐋, nothing}}, 3}:
  [:, :, 1] =
   -20.0 km  -20.0 km  -20.0 km  -20.0 km
   -20.0 km  -20.0 km  -20.0 km  -20.0 km
   -20.0 km  -20.0 km  -20.0 km  -20.0 km

  [:, :, 2] =
   -15.0 km  -15.0 km  -15.0 km  -15.0 km
   -15.0 km  -15.0 km  -15.0 km  -15.0 km
   -15.0 km  -15.0 km  -15.0 km  -15.0 km

  [:, :, 3] =
   -10.0 km  -10.0 km  -10.0 km  -10.0 km
   -10.0 km  -10.0 km  -10.0 km  -10.0 km
   -10.0 km  -10.0 km  -10.0 km  -10.0 km
julia> Data        =   zeros(size(Lon3D));
julia> Data_set    =   GeophysicalModelGenerator.GeoData(Lon3D,Lat3D,Depth3D,(DataFieldName=Data,))
GeoData
  size      : (3, 4, 3)
  lon       ϵ [ 11.0 : 19.0]
  lat       ϵ [ 1.0 : 10.0]
  depth     ϵ [ -20.0 km : -10.0 km]
  fields    : (:DataFieldName,)
  attributes: ["note"]
```
