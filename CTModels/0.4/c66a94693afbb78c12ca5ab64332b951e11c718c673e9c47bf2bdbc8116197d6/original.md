```julia
plot(
    sol::CTModels.AbstractSolution,
    description::Symbol...;
    kwargs...
)

```

Plot a solution from an optimal control problem.

This function dispatches on a solution type that inherits from `AbstractSolution`. It is intended to visualize various components of the solution (such as state trajectories, controls, costates, or any other variables defined in the model).

!!! note
    This function requires the `Plots.jl` package to be available. If it is not loaded, a `CTBase.ExtensionError(:Plots)` is thrown.


# Arguments

  * `sol::AbstractSolution`: A solution object returned by solving a control problem.
  * `description::Symbol...`: Optional symbols specifying what to plot (e.g., `:state`, `:control`, `:costate`, etc.). If empty, a default set of components is plotted.
  * `kwargs...`: Additional keyword arguments passed to the underlying plotting routines (e.g., `xlabel`, `ylabel`, `legend`, etc.).

# Returns

  * A plot object (if `Plots.jl` is available) visualizing the selected components of the solution.

# Example

```julia-repl
julia> using Plots
julia> plot(sol, :state, :control, xlabel = "Time", layout = (2,1))
```

# Throws

  * `CTBase.ExtensionError` if the `Plots` package is not available or not loaded.
