```
plot(elements::ElementOrFunctionOrLayers...; aesthetics...) -> Plot
```

'aesthetics'のベクトルの新しいプロットを作成します。オプションの`elements`（[Scales](@ref lib_scale), [Statistics](@ref lib_stat), [Coordinates](@ref lib_coord), [Geometries](@ref lib_geom), [Guides](@ref lib_guide), [Themes](@ref), および/または[Layers](@ref)）は、データのレイアウト、ラベル付け、および変換を制御します。

# 例

```
plot(x=collect(1917:2018), y=1.02.^(0:101), Geom.line)
```
