```
plot_fuel!(plot, results)
```

Plots a stack plot of the results by fuel type and assigns each fuel type a specific color.

# Arguments

  * `plot`: existing plot handle, such as the result of [`plot()`](@extref RecipesBase.plot) (optional)
  * `res::`[`InfrastructureSystems.Results`](@extref):    A `Results` object (e.g., [`PowerSimulations.SimulationProblemResults`](@extref))   to be plotted

# Accepted Key Words

  * `generator_mapping_file` = "file_path" : file path to yaml defining generator category by fuel and primemover
  * `variables::Union{Nothing, Vector{Symbol}}` = nothing : specific variables to plot
  * `slacks::Bool = true` : display slack variables
  * `load::Bool = true` : display load line
  * `curtailment::Bool = true`: To plot the curtailment in the stack plot
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
  * `palette` : Color palette as from [`load_palette`](@ref).
