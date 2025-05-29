```
struct LevelSetCutter <: Cutter end
```

`DiscreteGeometry` と `AnalyticalGeometry` のためのカッター。

## 使用法

```
cut(background::DiscreteModel,geom::AnalyticalGeometry)
cut(background::DiscreteModel,geom::DiscreteGeometry)
cut_facets(background::DiscreteModel,geom::AnalyticalGeometry)
cut_facets(background::DiscreteModel,geom::DiscreteGeometry)
```
