```
PlotOptions(Plots; kwargs...)
```

If `PlotOptions` is passed to `BossOptions` as `callback`, the state of the optimization problem is plotted in each iteration. Only works with one-dimensional `x` domains but supports multi-dimensional `y`.

# Arguments

  * `Plots::Module`: Evaluate `using Plots` and pass the `Plots` module to `PlotsOptions`.

# Keywords

  * `f_true::Union{Nothing, Function}`: The true objective function to be plotted.
  * `points::Int`: The number of points in each plotted function.
  * `xaxis::Symbol`: Used to change the x axis scale (`:identity`, `:log`).
  * `yaxis::Symbol`: Used to change the y axis scale (`:identity`, `:log`).
  * `title::String`: The plot title.
