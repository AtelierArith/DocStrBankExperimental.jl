```
integrate_lonlat(var::OutputVar)
```

Integrate `data` in `var` on longitude and latitude with a first-order scheme. `data` has to be discretized on longitude and latitude.

If the points are equispaced, it is assumed that each point correspond to the midpoint of a cell which results in rectangular integration using the midpoint rule. Otherwise, the integration being done is rectangular integration using the left endpoints for integrating longitude and latitude. The units for longitude and latitude should be degrees.

All `NaN`s in `var.data` are treated as zeros when integrating.
