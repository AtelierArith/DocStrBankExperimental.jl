```julia
NonlinearSystem(
    sys::ModelingToolkit.AbstractODESystem
) -> Any

```

Convert an `ODESystem` to a `NonlinearSystem` solving for its steady state (where derivatives are zero). Any differential variable `D(x) ~ f(...)` will be turned into `0 ~ f(...)`. The returned system is not simplified. If the input system is `complete`d, then so will the returned system.
