```
plot_demand!(plot, result)
plot_demand!(plot, system)
```

Plots the demand in the system.

# Arguments

  * `plot`: existing plot handle, such as the result of [`plot()`](@extref RecipesBase.plot)
  * `res::Union{`[`InfrastructureSystems.Results`](@extref)`,`[`PowerSystems.System`](@extref)`}`:    A `Results` object (e.g., [`PowerSimulations.SimulationProblemResults`](@extref))   or [`PowerSystems.System`](@extref) to plot the demand from

# Accepted Key Words

  * `linestyle::Symbol = :dash` : set line style
  * `title::String`: Set a title for the plots
  * `horizon::Int64`: To plot a shorter window of time than the full results
  * `initial_time::DateTime`: To start the plot at a different time other than the results initial time
  * `aggregate::String = "System", "PowerLoad", or "Bus"`: aggregate the demand by   [`PowerSystems.System`](@extref), [`PowerSystems.PowerLoad`](@extref), or [`PowerSystems.Bus`](@extref),   rather than by generator
  * `set_display::Bool = true`: set to false to prevent the plots from displaying
  * `save::String = "file_path"`: set a file path to save the plots
  * `format::String = "png"`: set a different format for saving a [PlotlyJS](@extref Plots [Plotly-/-PlotlyJS](https://github.com/spencerlyon2/PlotlyJS.jl)) plot. Options include "png", "pdf" and "eps"
  * `seriescolor::Array`: Set different colors for the plots
  * `title::String = "Title"`: Set a title for the plots
  * `stack::Bool = true`: stack plot traces
  * `bar::Bool` : create bar plot
  * `nofill::Bool` : force empty area fill
  * `stair::Bool`: Make a stair plot instead of a stack plot
  * `filter_func::Function =`[`PowerSystems.get_available`](@extref PowerSystems.get_available-Tuple{Component}): filter components included in plot
  * `palette` : color palette from [`load_palette`](@ref)
