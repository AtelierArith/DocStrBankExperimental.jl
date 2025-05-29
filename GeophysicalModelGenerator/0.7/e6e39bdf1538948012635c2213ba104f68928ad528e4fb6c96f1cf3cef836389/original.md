```
CartData(x::Any, y::Any, z::GeoUnit, fields::NamedTuple)
```

Data structure that holds one or several fields with with Cartesian x/y/z coordinates. Distances are in kilometers

  * `x`,`y`,`z` can have units of meters, kilometer or be unitless; they will be converted to kilometers
  * `fields` should ideally be a NamedTuple which allows you to specify the names of each of the fields.
  * In case you only pass one array we will convert it to a NamedTuple with default name.
  * A single field should be added as `(DataFieldName=Data,)` (don't forget the comma at the end).
  * Multiple fields  can be added as well.
  * In case you want to display a vector field in paraview, add it as a tuple: `(Velocity=(Vx,Vnorth,Vup), Veast=Veast, Vnorth=Vnorth, Vup=Vup)`; we automatically apply a vector transformation when transforming this to a `ParaviewData` structure from which we generate Paraview output. As this changes the magnitude of the arrows, you will no longer see the `[Veast,Vnorth,Vup]` components in Paraview which is why it is a good ideas to store them as separate Fields.
  * Yet, there is one exception: if the name of the 3-component field is `colors`, we do not apply this vector transformation as this field is regarded to contain RGB colors.
  * `x`,`y`,`z` should have the same size as the `Data` array. The ordering of the arrays is important. If they are 3D arrays, as in the example below, we assume that the first dimension corresponds to `x`, second dimension to `y` and third dimension to `z` (which should be in km). See below for an example.

# Example

```julia-repl
julia> x        =   0:2:10
julia> y        =   -5:5
julia> z        =   -10:2:2
julia> X,Y,Z    =   xyz_grid(x, y, z);
julia> Data     =   Z
julia> Data_set =   CartData(X,Y,Z, (FakeData=Data,Data2=Data.+1.))
CartData
    size    : (6, 11, 7)
    x       ϵ [ 0.0 km : 10.0 km]
    y       ϵ [ -5.0 km : 5.0 km]
    z       ϵ [ -10.0 km : 2.0 km]
    fields  : (:FakeData, :Data2)
  attributes: ["note"]
```

`CartData` is particularly useful in combination with cartesian geodynamic codes, such as LaMEM, which require cartesian grids. You can directly save your data to Paraview with

```julia-repl
julia> write_paraview(Data_set, "Data_set")
1-element Vector{String}:
 "Data_set.vts"
```

If you wish, you can convert this to `UTMData` (which will simply convert the )

```julia-repl
julia> Data_set1 =  convert(GeoData, Data_set)
GeoData
  size  : (116, 96, 25)
  lon   ϵ [ 14.075969111533457 : 14.213417764154963]
  lat   ϵ [ 40.77452227533946 : 40.86110443583479]
  depth ϵ [ -5.4 km : 0.6 km]
  fields: (:FakeData, :Data2)
```

which would allow visualizing this in paraview in the usual manner:
