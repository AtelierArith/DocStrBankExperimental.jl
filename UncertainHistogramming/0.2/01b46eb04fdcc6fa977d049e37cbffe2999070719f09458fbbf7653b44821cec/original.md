```
abstract type ContinuousHistogram end
```

`abstract type` representing the `ContinuousHistogram` concept. These are histograms whose input data have *uncertainty* associated with them, and therefore we build them using a value-error-dependent kernel for each entry.

For each new `ContinuousHistogram`, one *must* overload the functions given in each of the `src/Kernels` folder. Then one  needs to add a new [`ContinuousDistribution`](@ref) and define its methods, like those shown in the `src/Moments` files. Finally, the [`KernelDistribution`](@ref) must be mapped.

Then all `util`ity and `stats` functionality should *just work*.

!!! note
    In this context, *continuity* refers to the domain of the histogram, and not necessarily its range.

