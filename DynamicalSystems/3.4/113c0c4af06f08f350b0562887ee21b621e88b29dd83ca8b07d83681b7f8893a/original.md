```
interactive_trajectory_timeseries(ds::DynamicalSystem, fs, [, u0s]; kwargs...) → fig, dsobs
```

Create a Makie `Figure` to visualize trajectories and timeseries of observables of `ds`. This `Figure` can also be used as an interactive GUI to enable interactive control over parameters and time evolution. It can also be used to create videos, as well as customized animations, see below.

`fs` is a `Vector` of "indices to observe", i.e., anything that can be given to [`observe_state`](@ref). Each observation index will make a timeseries plot. `u0s` is a `Vector` of initial conditions. Each is evolved with a unique color and displayed both as a trajectory in state space and as an observed timeseries. Elements of `u0` can be either `Vector{Real}` encoding a full state or `Dict` to partially set a state from current state of `ds` (same as in [`set_state!`](@ref)).

The trajectories from the initial conditions in `u0s` are all evolved and visualized in parallel. By default only the current state of the system is used. `u0s` can be anything accepted by a [`ParallelDynamicalSystem`](@ref).

## Return

Return `fig, dsobs::DynamicalSystemObservable`. `fig` is the created `Figure`. `dsobs` facilities the creation of custom animations and/or interactive applications, see the custom animations section below.

See also [`interactive_trajectory`](@ref).

## Interactivity and time stepping keywords

!!! note "GLMakie"
    GUI functionality is possible when the plotting backend is `GLMakie` or `WGLMakie`. Do `using GLMakie; GLMakie.activate!()` to ensure this is the chosen backend.


  * `add_controls = true`: If `true`, below the state space axis some buttons for animating the trajectories live are added:

      * "reset": results the parallel trajectories to their initial conditions.
      * "run": when clicked it evolves the trajectories forwards in time indefinitely. click again to stop the evolution. Note that "run" simply presses the "step" button indefinitely, and hence the visual progress you see on the screen depends on the value of the "steps" slider. Thus, while the animation "runs" you can increase/decrease the "steps" slider to increase/decrease the animation speed. For smooth animations for continuous time systems you should have small `Δt` and large `tail`.
      * "step": when clicked it evolves the trajectories forwards in time for the amount of steps chosen by the "steps" slider to its right. Each step is an evolution of `Δt` unit of time long (and clicking the "step" button may do more than one steps according to the slider).

    The plotted trajectories can always be evolved manually using the custom animations setup that we describe below; `add_controls` only concerns the buttons and interactivity added to the created figure.
  * `parameter_sliders = nothing`: If given, it must be a dictionary, mapping parameter indices (any valid index that can be given to [`set_parameter!`](@ref)) to ranges of parameter values. Each combination of index and range becomes a slider that can be interactively controlled to alter a system parameter on the fly during time evolution. Below the parameter sliders, three buttons are added for GUI usage:

      * "update": when clicked the chosen parameter values are propagated into the system.
      * "u.r.s.": when clicked it is equivalent with clicking in order: "update", "reset", "step".
      * "reset p": when clicked it resets parameters to their initial values.

    Parameters can also be altered using the custom animation setup that we describe below; `parameter_sliders` only conserns the buttons and interactivity added to the created figure.
  * `parameter_names = Dict(keys(ps) .=> string.(keys(ps)))`: Dictionary mapping parameter keys to labels. Only used if `parameter_sliders` is given.
  * `Δt`: Time step of time evolution. Defaults to 1 for discrete time, 0.01 for continuous time systems. Continuous time dynamical systems are stepped for exactly `Δt` time (third argument to `step!` is `true`).
  * `pause = nothing`: If given, it must be a real number. This number is given to the `sleep` function, which is called between each plot update. Useful when time integration is computationally inexpensive and animation proceeds too fast.
  * `starting_step = 1`: the starting value of the "step" slider.

## Visualization keywords

  * `colors`: The color for each initial condition (and resulting trajectory and timeseries). Needs to be a `Vector` of equal length as `u0s`.
  * `tail = 1000`: Length of plotted trajectory (in units of `Δt`).
  * `fade = 0.5`: The trajectories in state space are faded towards full transparency. The alpha channel (transparency) scales as `t^fade` with `t` ranging from 0 to 1 (1 being the end of the trajectory). Use `fade = 1.0` for linear fading or `fade = 0` for no fading. Current default makes fading progress faster at trajectory start and slower at trajectory end.
  * `markersize = 15`: Size of markers of trajectory endpoints. For discrete systems half of that is used for the trajectory tail.
  * `plotkwargs = NamedTuple()`: A named tuple of keyword arguments propagated to the state space plot (`lines` for continuous, `scatter` for discrete systems). `plotkwargs` can also be a vector of named tuples, in which case each initial condition gets different arguments.

## Statespace trajectory keywords

  * `idxs = 1:min(length(u0s[1]), 3)`: Which variables to plot in a state space trajectory. Any index that can be given to [`observe_state`](@ref) can be given here.
  * `statespace_axis = true`: Whether to create and display an axis for the trajectory plot.
  * `idxs = 1:min(length(u0s[1]), 3)`: Which variables to plot in a state space trajectory. Any index that can be given to [`observe_state`](@ref) can be given here. If three indices are given, the trajectory plot is also 3D, otherwise 2D.
  * `lims`: A tuple of tuples (min, max) for the axis limits. If not given, they are automatically deduced by evolving each of `u0s` 1000 `Δt` units and picking most extreme values (limits are *not* adjusted by default during the live animations).
  * `figure, axis`: both can be named tuples with arbitrary keywords propagated to the generation of the `Figure` and state space `Axis` instances.

## Timeseries keywords

  * `linekwargs = NamedTuple()`: Extra keywords propagated to the timeseries plots. Can also be a vector of named tuples, each one for each unique initial condition.
  * `timeseries_names`: A vector of strings with length equal to `fs` giving names to the y-labels of the timeseries plots.
  * `timeseries_ylims`: A vector of 2-tuples for the lower and upper limits of the y-axis of each timeseries plot. If not given it is deduced automatically similarly to `lims`.
  * `timeunit = 1`: the units of time, if any. Sets the units of the timeseries x-axis.
  * `timelabel = "time"`: label of the x-axis of the timeseries plots.

## Custom animations

The second return argument `dsobs` is a `DynamicalSystemObservable`. The trajectories plotted in the main panel are linked to observables that are fields of the `dsobs`. Specifically, the field `dsobs.state_obserable` is an observable containing the final state of each of the trajectories, i.e., a vector of vectors like `u0s`. `dsobs.param_observable` is an observable of the system parameters. These observables are triggered by the interactive GUI buttons (the first two when the system is stepped in time, the last one when the parameters are updated). However, these observables, and hence the corresponding plotted trajectories that are `map`ed from these observables, can be updated via the formal API of `DynamicalSystem`:

```
step!(dsobs, n::Int = 1)
```

will step the system for `n` steps of `Δt` time, and only update the plot on the last step. `set_parameter!(dsobs, index, value)` will update the system parameter and then trigger the parameter observable. Lastly, `set_state!(dsobs, new_u [, i])` will set the `i`-th system state and clear the trajectory plot to the new initial condition.

This information can be used to create custom animations and/or interactive apps. In principle, the only thing a user has to do is create new observables from the existing ones using e.g. the `on` function and plot these new observables. Various examples are provided in the online documentation.
