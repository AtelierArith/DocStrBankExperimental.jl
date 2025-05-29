```
plot(elements::ElementOrFunctionOrLayers...; aesthetics...) -> Plot
```

Create a new plot of the vectors in 'aesthetics'.  Optional `elements` ([Scales](@ref lib_scale), [Statistics](@ref lib_stat), [Coordinates](@ref lib_coord), [Geometries](@ref lib_geom), [Guides](@ref lib_guide), [Themes](@ref), and/or [Layers](@ref)) control the layout, labelling, and transformation of the data.

# Examples

```
plot(x=collect(1917:2018), y=1.02.^(0:101), Geom.line)
```
