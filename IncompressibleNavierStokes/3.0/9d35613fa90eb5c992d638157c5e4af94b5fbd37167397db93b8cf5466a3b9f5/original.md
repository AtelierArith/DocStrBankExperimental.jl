```julia
solve_unsteady(
;
    setup,
    tlims,
    ustart,
    tempstart,
    method,
    psolver,
    Δt,
    Δt_min,
    cfl,
    n_adapt_Δt,
    docopy,
    processors,
    θ,
    cache
)

```

Solve unsteady problem using `method`.

If `Δt` is a real number, it is rounded such that `(t_end - t_start) / Δt` is an integer. If `Δt = nothing`, the time step is chosen every `n_adapt_Δt` iteration with CFL-number `cfl`. If `Δt_min` is given, the adaptive time step never goes below it.

The `processors` are called after every time step.

Note that the `state` observable passed to the `processor.initialize` function contains vector living on the device, and you may have to move them back to the host using `Array(u)` in the processor.

Return `(; u, t), outputs`, where `outputs` is a  named tuple with the outputs of `processors` with the same field names.
