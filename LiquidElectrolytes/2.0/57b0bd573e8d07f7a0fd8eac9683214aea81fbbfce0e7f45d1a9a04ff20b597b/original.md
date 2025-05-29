```
function dlcapsweep(
        sys;
        electrolyte = electrolytedata(sys),
        inival = nothing,
        voltages = (-1:0.1:1) * ufac"V",
        δ = 1.0e-4,
        store_solutions = false,
        solver_kwargs...
    )
```

Calculate double layer capacitances for voltages given in `voltages`. Returns a [`DLCapSweepResult`](@ref).

Assumptions:

  * Only one double layer in the system - close to working electrode.
