```julia
VectorContinuousCallback(condition, affect!, affect_neg!, len;
    initialize = INITIALIZE_DEFAULT,
    finalize = FINALIZE_DEFAULT,
    idxs = nothing,
    rootfind = LeftRootFind,
    save_positions = (true, true),
    interp_points = 10,
    abstol = 10eps(), reltol = 0, repeat_nudge = 1 // 100,
    initializealg = nothing)
```

```julia
VectorContinuousCallback(condition, affect!, len;
    initialize = INITIALIZE_DEFAULT,
    finalize = FINALIZE_DEFAULT,
    idxs = nothing,
    rootfind = LeftRootFind,
    save_positions = (true, true),
    affect_neg! = affect!,
    interp_points = 10,
    abstol = 10eps(), reltol = 0, repeat_nudge = 1 // 100,
    initializealg = nothing)
```

This is also a subtype of `AbstractContinuousCallback`. `CallbackSet` is not feasible when you have many callbacks, as it doesn't scale well. For this reason, we have `VectorContinuousCallback` - it allows you to have a single callback for multiple events.

# Arguments

  * `condition`: This is a function `condition(out, u, t, integrator)` which should save the condition value in the array `out` at the right index. Maximum index of `out` should be specified in the `len` property of callback. So, this way you can have a chain of `len` events, which would cause the `i`th event to trigger when `out[i] = 0`.
  * `affect!`: This is a function `affect!(integrator, event_index)` which lets you modify `integrator` and it tells you about which event occurred using `event_idx` i.e. gives you index `i` for which `out[i]` came out to be zero.
  * `len`: Number of callbacks chained. This is compulsory to be specified.

Rest of the arguments have the same meaning as in [`ContinuousCallback`](@ref).
