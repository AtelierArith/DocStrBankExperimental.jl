```julia
struct Pose3 <: DistributedFactorGraphs.InferenceVariable
```

Pose3 is currently a Euler angle mechanization of three Euclidean translations and three Circular rotation.

## Future:

  * Work in progress on AMP3D for proper non-Euler angle on-manifold operations.
  * TODO the AMP upgrade is aimed at resolving 3D to Quat/SE3/SP3 – current Euler angles will be replaced
