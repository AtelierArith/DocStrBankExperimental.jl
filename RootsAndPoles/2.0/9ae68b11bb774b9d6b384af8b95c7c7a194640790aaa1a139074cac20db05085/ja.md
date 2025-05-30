```
grpf(fcn, origcoords, ::PlotData, params=GRPFParams())
```

`grpf`のバリアントで、`zroots`と`zpoles`に加えて、`quadrants`、`phasediffs`、`VoronoiDelauany`タイル化`tess`、および`VoronoiDelaunay`から関数空間への変換のための`Geometry2Function`構造体`g2f`を返します。

これらの追加出力は主にプロットや診断のためのものです。

# 例

```
julia> roots, poles, quadrants, phasediffs, tess, g2f = grpf(simplefcn, origcoords, PlotData());
```
