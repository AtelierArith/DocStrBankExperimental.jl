```
render!(c::Cell, p::Polygon, meta::GDSMeta=GDSMeta())
```

Render a polygon `p` to cell `c`, defaulting to plain styling. If `p` has more than 8190 (set by DeviceLayout's `GDS_POLYGON_MAX` constant), then it is partitioned into smaller polygons which are then rendered. Environment variable `ENV["GDS_POLYGON_MAX"]` will override this constant. The partitioning algorithm implements guillotine cutting, that goes through at least one existing vertex and in manhattan directions. Cuts are selected by ad hoc optimzation for "nice" partitions.
