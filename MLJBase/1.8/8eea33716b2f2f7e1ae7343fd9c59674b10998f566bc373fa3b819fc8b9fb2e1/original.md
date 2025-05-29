```
resampler = Resampler(
    model=ConstantRegressor(),
    resampling=CV(),
    measure=nothing,
    weights=nothing,
    class_weights=nothing
    operation=predict,
    repeats = 1,
    acceleration=default_resource(),
    check_measure=true,
    per_observation=true,
    logger=default_logger(),
    compact=false,
)
```

*Private method.* Use at own risk.

Resampling model wrapper, used internally by the `fit` method of `TunedModel` instances and `IteratedModel` instances. See [`evaluate!`](@ref) for meaning of the options. Not intended for use by general user, who will ordinarily use [`evaluate!`](@ref) directly.

Given a machine `mach = machine(resampler, args...)` one obtains a performance evaluation of the specified `model`, performed according to the prescribed `resampling` strategy and other parameters, using data `args...`, by calling `fit!(mach)` followed by `evaluate(mach)`.

On subsequent calls to `fit!(mach)` new train/test pairs of row indices are only regenerated if `resampling`, `repeats` or `cache` fields of `resampler` have changed. The evolution of an RNG field of `resampler` does *not* constitute a change (`==` for `MLJType` objects is not sensitive to such changes; see [`is_same_except`](@ref)).

If there is single train/test pair, then warm-restart behavior of the wrapped model `resampler.model` will extend to warm-restart behaviour of the wrapper `resampler`, with respect to mutations of the wrapped model.

The sample `weights` are passed to the specified performance measures that support weights for evaluation. These weights are not to be confused with any weights bound to a `Resampler` instance in a machine, used for training the wrapped `model` when supported.

The sample `class_weights` are passed to the specified performance measures that support per-class weights for evaluation. These weights are not to be confused with any weights bound to a `Resampler` instance in a machine, used for training the wrapped `model` when supported.
