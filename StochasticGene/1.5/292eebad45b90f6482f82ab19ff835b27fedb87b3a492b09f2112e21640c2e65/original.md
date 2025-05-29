```
set_indices(ntransitions, R, S, insertstep)
set_indices(ntransitions, R)
set_indices(ntransitions)
set_indices(ntransitions, R, S, insertstep, offset)
```

Return an `Indices` structure based on the provided parameters.

# Description

This function returns an `Indices` structure based on the provided parameters. It can handle different combinations of `ntransitions`, `R`, `S`, `insertstep`, and `offset`.

# Arguments

  * `ntransitions`: Number of transitions.
  * `R`: Number of reporters.
  * `S`: Number of states.
  * `insertstep`: Insert step.
  * `offset`: Offset value (optional).

# Methods

  * `set_indices(ntransitions, R, S, insertstep)`: Computes the `Indices` structure based on the given parameters.
  * `set_indices(ntransitions, R)`: Computes the `Indices` structure based on `ntransitions` and `R`.
  * `set_indices(ntransitions)`: Computes the `Indices` structure based on `ntransitions`.
  * `set_indices(ntransitions, R, S, insertstep, offset)`: Computes the `Indices` structure based on the given parameters with an offset.

# Returns

  * `Indices`: The computed `Indices` structure.
