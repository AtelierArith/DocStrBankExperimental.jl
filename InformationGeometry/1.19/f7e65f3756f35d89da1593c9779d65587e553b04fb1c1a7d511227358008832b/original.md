```
CoordinateDistortion(DM::AbstractDataModel, Confnum::Real=1) -> Real
```

For CoordinateDistortions ≪ 1, the model predictions are extremely sensitive with respect to the parameters. For CoordinateDistortion ⪎ 1, the model is comparatively insensitive towards the parameters.

This quantity is computed from the ratio of the coordinate-dependent apparent volume of a confidence region compared with the coordinate-invariant volume, which is obtained from integrating over the appropriate volume form / geometric density factor. The unit of this quantity is $[L^n]$ where $L$ is the unit of length of each of the components.
