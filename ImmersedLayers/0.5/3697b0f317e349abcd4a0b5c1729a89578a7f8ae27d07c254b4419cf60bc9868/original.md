```
AreaForcingModel(model_function!)
```

Creates area-type forcing over the entire domain, using a `model_function!` (a function   that returns the strength of the forcing).

`model_function!` must be in-place with a signature of the form

```
  model_function!(str,state,t,fcache,phys_params)
```

where `str` is the strength to be returned, `state` the state vector,   `t` is time, `fcache` is a corresponding `AreaRegionCache`   and `phys_params` are user-supplied physical parameters. Any of these can   be utilized to compute the strength.

The keyword `spatialfield =` can provide   an `AbstractSpatialField` to help in evaluating the strength.   (The resulting field is available to `model_function!` in the `generated_field` field     of `fcache`.)
