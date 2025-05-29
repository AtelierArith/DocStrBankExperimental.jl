```
  PointForcingModel(pts::VectorData,transform::MotionTransform,model_function!)
```

Bundles point coordinates `pts`, a `transform` (to specify where the origin of the points'   coordinate system is relative to the inertial system's origin), and a `model_function!` (a function   that returns the strength of the forcing) for point-type forcing.   `model_function!` must be in-place with a signature of the form

```
  model_function!(str,state,t,fcache,phys_params)
```

where `str` is the strength to be returned, `state` the state vector,   `t` is time, `fcache` is a corresponding `PointRegionCache`   and `phys_params` are user-supplied physical parameters. Any of these can   be utilized to compute the strength.

The keyword `ddftype =` can be used to specify the type of DDF.
