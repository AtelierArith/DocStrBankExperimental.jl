```
(mapS3D::MapS3D)(alt::Real = mapS3D.alt[1])
```

Get scalar magnetic anomaly map at specific altitude.

**Arguments:**

  * `mapS3D`: `MapS3D` 3D (multi-level) scalar magnetic anomaly map struct
  * `alt`:    (optional) map altitude [m]

**Returns:**

  * `mapS`: `MapS` scalar magnetic anomaly map struct at `alt`
