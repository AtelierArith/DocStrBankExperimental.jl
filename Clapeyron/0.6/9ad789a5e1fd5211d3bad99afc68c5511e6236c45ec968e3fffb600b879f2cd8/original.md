```
Tt,pt,vs,vl,vv = triple_point(model::CompositeModel;v0 = x0_triple_point(model))
```

Calculates the triple point of a `CompositeModel` containing solid and fluid phase EoS.

returns:

  * Triple point Temperature [`K`]
  * Triple point Pressure [`Pa`]
  * solid volume at Triple Point [`m³`]
  * liquid volume at Triple Point [`m³`]
  * vapour volume at Triple Point [`m³`]
