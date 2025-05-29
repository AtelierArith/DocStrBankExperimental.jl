```
  AreaForcingModel(shape::Union{Body,BodyList},transform::MotionTransform,model_function!)
```

Bundles a `shape` (i.e., a `Body`, `BodyList`,), a `transform` (to specify where to   place the shape), and a `model_function!` (a function   that returns the strength of the forcing) for area-type forcing.   `model_function!` must be in-place with a signature of the form

```
  model_function!(str,state,t,fcache,phys_params)
```

where `str` is the strength to be returned, `state` the state vector,   `t` is time, `fcache` is a corresponding `AreaRegionCache`   and `phys_params` are user-supplied physical parameters. Any of these can   be utilized to compute the strength.

There are a number of keyword arguments that can be passed in:   `ddftype =`,specifying the type of DDF; `spatialfield =` to provide   an `AbstractSpatialField` to help in evaluating the strength.   (The resulting field is available to `model_function!` in the `generated_field` field     of `fcache`.)
