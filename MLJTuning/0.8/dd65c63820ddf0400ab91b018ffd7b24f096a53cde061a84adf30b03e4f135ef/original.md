```
LatinHypercube(gens = 1,
               popsize = 100,
               ntour = 2,
               ptour = 0.8.,
               interSampleWeight = 1.0,
               ae_power = 2,
               periodic_ae = false,
               rng=Random.GLOBAL_RNG)
```

Instantiate grid-based hyperparameter tuning strategy using the library [LatinHypercubeSampling.jl](https://github.com/MrUrq/LatinHypercubeSampling.jl).

An optimised Latin Hypercube sampling plan is created using a genetic based optimization algorithm based on the inverse of the Audze-Eglais function.  The optimization is run for `nGenerations` and creates `n` models for evaluation, where `n` is specified by a corresponding `TunedModel` instance, as in

```
tuned_model = TunedModel(model=...,
                         tuning=LatinHypercube(...),
                         range=...,
                         measures=...,
                         n=...)
```

(See [`TunedModel`](@ref) for complete options.)

To use a periodic version of the Audze-Eglais function (to reduce clustering along the boundaries) specify `periodic_ae = true`.

### Supported ranges:

A single one-dimensional range or vector of one-dimensioinal ranges can be specified. Specifically, in `LatinHypercubeSampling` search, the `range` field of a `TunedModel` instance can be:

  * A single one-dimensional range - ie, `ParamRange` object - `r`, constructed

using the `range` method.

  * Any vector of objects of the above form

Both `NumericRange`s and `NominalRange`s are supported, and hyper-parameter values are sampled on a scale specified by the range (eg, `r.scale = :log`).
