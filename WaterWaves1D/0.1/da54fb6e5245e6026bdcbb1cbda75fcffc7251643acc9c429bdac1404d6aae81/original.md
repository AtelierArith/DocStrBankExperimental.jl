```
Problem( model, initial, param ; solver, label)
```

Build an initial-value problem which can then be solved (i.e. integrated in time) through `solve!( problem )`

# Arguments

  * `model   :: AbstractModel`,  the system of equation solved.

May be built, e.g., by `WaterWaves(param)`;

  * `initial :: InitialData`, the initial data.

May be buit, e.g., by `Init(η,v)` where `η` is the surface deformation and `v` the derivative of the trace of the velocity potential at the surface;

  * `times :: Times` is the time grid, and may be built using the function `Times`.

Alternatively one can simply provide a `NamedTuple` with     - `T`, the final time of integration     - `dt`, the timestep     - optionally, `Ns` the number of computed data or `ns` for storing data every `ns` computation steps (by default, every computed data is stored).

## Optional keyword arguments

  * `solver :: TimeSolver`, the solver for time integration (default is explicit Runge-Kutta fourth order solver).

May be built, e.g., by `RK4(model)` or `RK4_naive()`.

  * `label   :: String` is used in future references (e.g. `plot_solution`).
  * Information are not printed if `verbose = false` (default is `true`).
