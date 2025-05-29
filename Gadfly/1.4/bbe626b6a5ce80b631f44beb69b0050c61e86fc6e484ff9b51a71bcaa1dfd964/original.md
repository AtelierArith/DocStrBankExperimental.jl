```
layer(data_source::Union{AbstractDataFrame, Void}),
      elements::ElementOrFunction...; mapping...) -> [Layers]
```

Create a layer element based on the data in `data_source`, to later input into `plot`.  `elements` can be [Statistics](@ref lib_stat), [Geometries](@ref lib_geom), and/or [Themes](@ref) (but not Scales, Coordinates, or Guides). `mapping` are aesthetics.

# Examples

```
ls=[]
append!(ls, layer(y=[1,2,3], Geom.line))
append!(ls, layer(y=[3,2,1], Geom.point))
plot(ls..., Guide.title("layer example"))
```
