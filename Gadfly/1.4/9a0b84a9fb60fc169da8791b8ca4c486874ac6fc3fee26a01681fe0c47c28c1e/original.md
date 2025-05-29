```
plot(data_source::Union{AbstractMatrix, AbstractDataFrame},
     elements::ElementOrFunctionOrLayers...; mapping...) -> Plot
```

Create a new plot by specifying a `data_source`, zero or more `elements` ([Scales](@ref lib_scale), [Statistics](@ref lib_stat), [Coordinates](@ref lib_coord), [Geometries](@ref lib_geom), [Guides](@ref lib_guide), [Themes](@ref), and/or [Layers](@ref)), and a `mapping` of aesthetics to columns or expressions of the data.

# Examples

```
my_frame = DataFrame(time=1917:2018, price=1.02.^(0:101))
plot(my_frame, x=:time, y=:price, Geom.line)

my_matrix = [1917:2018 1.02.^(0:101)]
plot(my_matrix, x=Col.value(1), y=Col.value(2), Geom.line,
     Guide.xlabel("time"), Guide.ylabel("price"))
```
