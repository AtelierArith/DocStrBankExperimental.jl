```
plot(data_source::Union{AbstractMatrix, AbstractDataFrame},
     elements::ElementOrFunctionOrLayers...; mapping...) -> Plot
```

`data_source`を指定し、ゼロ個以上の`elements`（[Scales](@ref lib_scale), [Statistics](@ref lib_stat), [Coordinates](@ref lib_coord), [Geometries](@ref lib_geom), [Guides](@ref lib_guide), [Themes](@ref), および/または [Layers](@ref)）を指定し、データの列または式に対する美的要素の`mapping`を指定することで新しいプロットを作成します。

# 例

```
my_frame = DataFrame(time=1917:2018, price=1.02.^(0:101))
plot(my_frame, x=:time, y=:price, Geom.line)

my_matrix = [1917:2018 1.02.^(0:101)]
plot(my_matrix, x=Col.value(1), y=Col.value(2), Geom.line,
     Guide.xlabel("time"), Guide.ylabel("price"))
```
