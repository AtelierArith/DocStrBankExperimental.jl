```
Callback(func, schedule=IterationInterval(1);
         parameters=nothing, callsite=TimeStepCallsite())
```

Return `Callback` that executes `func` on `schedule` at the `callsite` with optional `parameters`. By default, `schedule = IterationInterval(1)` and `callsite = TimeStepCallsite()`.

If `isnothing(parameters)`, `func(sim::Simulation)` is called. Otherwise, `func` is called via `func(sim::Simulation, parameters)`.

The `callsite` determines where `Callback` is executed. The possible values for `callsite` are

  * `TimeStepCallsite()`: after a time-step.
  * `TendencyCallsite()`: after tendencies are calculated, but before taking a time-step (useful for modifying tendency calculations).
  * `UpdateStateCallsite()`: within `update_state!`, after auxiliary variables have been computed (for multi-stage time-steppers, `update_state!` may be called multiple times per time-step).
