```
judiProjection(geometry)
```

Projection operator for sources/receivers to restrict or inject data at specified locations.

# Examples

`F` is a modeling operator of type `judiModeling` and `q` is a seismic source of type `judiVector`:     Pr = judiProjection(rec_geometry)     Ps = judiProjection(q.geometry)     dobs = Pr*F*Ps'*q     qad = Ps*F'*Pr'*dobs
