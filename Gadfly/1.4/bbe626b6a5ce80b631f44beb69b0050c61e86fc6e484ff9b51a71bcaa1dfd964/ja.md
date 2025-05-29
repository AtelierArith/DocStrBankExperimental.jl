```
layer(data_source::Union{AbstractDataFrame, Void}),
      elements::ElementOrFunction...; mapping...) -> [Layers]
```

`data_source`のデータに基づいてレイヤー要素を作成し、後で`plot`に入力します。`elements`には[Statistics](@ref lib_stat)、[Geometries](@ref lib_geom)、および/または[Themes](@ref)を指定できます（ただし、Scales、Coordinates、またはGuidesは除きます）。`mapping`は美的要素です。

# 例

```
ls=[]
append!(ls, layer(y=[1,2,3], Geom.line))
append!(ls, layer(y=[3,2,1], Geom.point))
plot(ls..., Guide.title("layer example"))
```
