```
grpf(fcn, origcoords, ::PlotData, params=GRPFParams())
```

Variant of `grpf` that returns `quadrants`, `phasediffs`, the `VoronoiDelauany` tesselation `tess`, and the `Geometry2Function` struct `g2f` for converting from the `VoronoiDelaunay` to function space, in addition to `zroots` and `zpoles`.

These additional outputs are primarily for plotting or diagnostics.

# Examples

```
julia> roots, poles, quadrants, phasediffs, tess, g2f = grpf(simplefcn, origcoords, PlotData());
```
