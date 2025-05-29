```
  LineForcingModel(shape::Union{Body,BodyList},transform::MotionTransform,model_function!)
```

Bundles a `shape` (i.e., a `Body`, `BodyList`,), a `transform` (to specify where to   place the shape), and a `model_function!` (a function   that returns the strength of the forcing) for line-type forcing.   `model_function!` must be in-place with a signature of the form

```
  model_function!(str,state,t,fcache,phys_params)
```

where `str` is the strength to be returned, `state` the state vector,   `t` is time, `fcache` is a corresponding `LineRegionCache`   and `phys_params` are user-supplied physical parameters. Any of these can   be utilized to compute the strength.

The keyword `ddftype =` can be used to specify the type of DDF.
