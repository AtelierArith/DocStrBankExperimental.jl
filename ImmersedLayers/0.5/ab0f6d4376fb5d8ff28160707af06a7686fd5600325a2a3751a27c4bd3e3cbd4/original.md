```
PointForcingModel(point_function::Function,transform::MotionTransform,model_function!::Function)
```

Bundles a `point_function` (a function that returns the positions of forcing points), a `transform` (to specify where the origin of the points' coordinate system is relative to the inertial system's origin), and a `model_function` (a function that returns the strength of the forcing) for point-type forcing.

`point_function` must have an out-of-place signature of the form

```
  point_function(state,t,fcache,phys_params)
```

where `state` the state vector, `t` is time, `fcache` is a corresponding `PointRegionCache`   and `phys_params` are user-supplied physical parameters. Any of these can   be utilized to compute the positions. It must return either a vector for   each coordinate or `VectorData`.

`model_function!` must have an in-place signature of the form

```
  model_function!(str,state,t,fcache,phys_params)
```

where `str` is the strength to be returned.
