```
UTMData(EW::Any, NS:Any, depth::GeoUnit, UTMZone::Int, NorthernHemisphere=true, fields::NamedTuple)
```

Data structure that holds one or several fields with UTM coordinates (east-west), (north-south) and depth information.

  * `depth` can have units of meters, kilometer or be unitless; it will be converted to meters (as UTMZ is usually in meters)
  * `fields` should ideally be a NamedTuple which allows you to specify the names of each of the fields.
  * In case you only pass one array we will convert it to a NamedTuple with default name.
  * A single field should be added as `(DataFieldName=Data,)` (don't forget the comma at the end).
  * Multiple fields  can be added as well.
  * In case you want to display a vector field in paraview, add it as a tuple: `(Velocity=(Veast,Vnorth,Vup), Veast=Veast, Vnorth=Vnorth, Vup=Vup)`; we automatically apply a vector transformation when transforming this to a `ParaviewData` structure from which we generate Paraview output. As this changes the magnitude of the arrows, you will no longer see the `[Veast,Vnorth,Vup]` components in Paraview which is why it is a good ideas to store them as separate Fields.
  * Yet, there is one exception: if the name of the 3-component field is `colors`, we do not apply this vector transformation as this field is regarded to contain RGB colors.
  * `Lat`,`Lon`,`Depth` should have the same size as the `Data` array. The ordering of the arrays is important. If they are 3D arrays, as in the example below, we assume that the first dimension corresponds to `lon`, second dimension to `lat` and third dimension to `depth` (which should be in km). See below for an example.

# Example

```julia-repl
julia> ew          =   422123.0:100:433623.0
julia> ns          =   4.514137e6:100:4.523637e6
julia> depth       =   -5400:250:600
julia> EW,NS,Depth =   xyz_grid(ew, ns, depth);
julia> Data        =   ustrip.(Depth);
julia> Data_set    =   UTMData(EW,NS,Depth,33, true, (FakeData=Data,Data2=Data.+1.))
UTMData
  UTM zone : 33-33 North
    size    : (116, 96, 25)
    EW      ϵ [ 422123.0 : 433623.0]
    NS      ϵ [ 4.514137e6 : 4.523637e6]
    depth   ϵ [ -5400.0 m : 600.0 m]
    fields  : (:FakeData, :Data2)
  attributes: ["note"]
```

If you wish, you can convert this from `UTMData` to `GeoData` with

```julia-repl
julia> Data_set1 =  convert(GeoData, Data_set)
GeoData
  size      : (116, 96, 25)
  lon       ϵ [ 14.075969111533457 : 14.213417764154963]
  lat       ϵ [ 40.77452227533946 : 40.86110443583479]
  depth     ϵ [ -5.4 km : 0.6 km]
  fields    : (:FakeData, :Data2)
  attributes: ["note"]
```

which would allow visualizing this in paraview in the usual manner:

```julia-repl
julia> write_paraview(Data_set1, "Data_set1")
1-element Vector{String}:
 "Data_set1.vts"
```
