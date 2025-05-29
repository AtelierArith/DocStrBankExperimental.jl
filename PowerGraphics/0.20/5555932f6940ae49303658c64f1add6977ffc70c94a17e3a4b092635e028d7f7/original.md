```
save_plot(plot, filename)
```

Saves plot to specified filename

# Arguments

  * `plot`: plot object
  * `filename::String` : save to filename

# Example

```julia
res = solve_op_problem!(OpProblem)
plot = plot_fuel(res)
save_plot(plot, "my_plot.png")
```

# Accepted Key Words (currently only implemented for [PlotlyJS](@extref Plots [Plotly-/-PlotlyJS](https://github.com/spencerlyon2/PlotlyJS.jl)) backend)

  * `width::Union{Nothing,Int}=nothing`
  * `height::Union{Nothing,Int}=nothing`
  * `scale::Union{Nothing,Real}=nothing`
