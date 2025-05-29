```
downward_L(mapS::Union{MapS,MapSd,MapS3D}, alt, α::Vector;
           expand::Bool = true)
```

Downward continuation using a sequence of regularization parameters to create a characteristic L-curve. The optimal regularization parameter is at a local minimum on the L-curve, which is a local maximum of curvature. The global maximum of curvature may or may not be the optimal regularization parameter.

**Arguments:**

  * `mapS`:   `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `alt`:    target downward continuation altitude [m]
  * `α`:      (geometric) sequence of regularization parameters
  * `expand`: (optional) if true, expand map temporarily to reduce edge effects

**Returns:**

  * `norms`: L-infinity norm of difference between sequential D.C. solutions
