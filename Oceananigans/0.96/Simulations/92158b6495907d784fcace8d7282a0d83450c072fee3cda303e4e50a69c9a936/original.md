```
conjure_time_step_wizard!(simulation, schedule=IterationInterval(5), wizard_kw...)
```

Add a `TimeStepWizard` built with `wizard_kw` as a `Callback` to `simulation`, called on `schedule` which is `IterationInterval(5)` by default.
