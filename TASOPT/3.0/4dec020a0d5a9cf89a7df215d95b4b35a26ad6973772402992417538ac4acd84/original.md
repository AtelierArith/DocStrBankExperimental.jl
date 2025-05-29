```
fly_mission!(ac, imission, itermax, initializes_engine)
```

Runs the aircraft through the specified mission, computing and converging the fuel weight. Formerly, `fly_offdesign_mission!()`.

!!! details "🔃 Inputs and Outputs"



**Inputs:**

  * `ac::aircraft`: Aircraft with first mission being the design mission
  * `imission::Int64`: Off design mission to run (Default: 1)
  * `itermax::Int64`: Maximum iterations for sizing loop
  * `initializes_engine::Boolean`: Use design case as initial guess for engine state if true

**Outputs:**

  * No explicit outputs. Computed quantities are saved to `par` arrays of `aircraft` model for the mission selected
