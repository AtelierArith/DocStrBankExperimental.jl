```
struct LevelSetCutter <: Cutter end
```

Cutter for `DiscreteGeometry` and `AnalyticalGeometry`.

## Usage

```
cut(background::DiscreteModel,geom::AnalyticalGeometry)
cut(background::DiscreteModel,geom::DiscreteGeometry)
cut_facets(background::DiscreteModel,geom::AnalyticalGeometry)
cut_facets(background::DiscreteModel,geom::DiscreteGeometry)
```
