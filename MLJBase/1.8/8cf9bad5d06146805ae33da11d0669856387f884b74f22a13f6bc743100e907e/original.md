```
MLJBase.fit_only!(
    mach::Machine;
    rows=nothing,
    verbosity=1,
    force=false,
    composite=nothing,
)
```

Without mutating any other machine on which it may depend, perform one of the following actions to the machine `mach`, using the data and model bound to it, and restricting the data to `rows` if specified:

  * *Ab initio training.* Ignoring any previous learned parameters and cache, compute and store new learned parameters. Increment `mach.state`.
  * *Training update.* Making use of previous learned parameters and/or  cache, replace or mutate existing learned parameters. The effect is  the same (or nearly the same) as in ab initio training, but may be  faster or use less memory, assuming the model supports an update  option (implements `MLJBase.update`). Increment `mach.state`.
  * *No-operation.* Leave existing learned parameters untouched. Do not  increment `mach.state`.

If the model, `model`, bound to `mach` is a symbol, then instead perform the action using the true model given by `getproperty(composite, model)`. See also [`machine`](@ref).

### Training action logic

For the action to be a no-operation, either `mach.frozen == true` or or none of the following apply:

1. `mach` has never been trained (`mach.state == 0`).
2. `force == true`.
3. The `state` of some other machine on which `mach` depends has changed since the last time `mach` was trained (ie, the last time `mach.state` was last incremented).
4. The specified `rows` have changed since the last retraining and `mach.model` does not have `Static` type.
5. `mach.model` is a model and different from the last model used for training, but has the same type.
6. `mach.model` is a model but has a type different from the last model used for training.
7. `mach.model` is a symbol and `(composite, mach.model)` is different from the last model used for training, but has the same type.
8. `mach.model` is a symbol and `(composite, mach.model)` has a different type from the last model used for training.

In any of the cases (1) - (4), (6), or (8), `mach` is trained ab initio. If (5) or (7) is true, then a training update is applied.

To freeze or unfreeze `mach`, use `freeze!(mach)` or `thaw!(mach)`.

### Implementation details

The data to which a machine is bound is stored in `mach.args`. Each element of `args` is either a `Node` object, or, in the case that concrete data was bound to the machine, it is concrete data wrapped in a `Source` node. In all cases, to obtain concrete data for actual training, each argument `N` is called, as in `N()` or `N(rows=rows)`, and either `MLJBase.fit` (ab initio training) or `MLJBase.update` (training update) is dispatched on `mach.model` and this data. See the "Adding models for general use" section of the MLJ documentation for more on these lower-level training methods.
