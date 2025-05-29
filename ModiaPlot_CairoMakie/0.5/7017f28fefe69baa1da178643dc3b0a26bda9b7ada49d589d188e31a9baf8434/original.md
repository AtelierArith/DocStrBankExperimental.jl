```
plot(result, names; 
     heading = "", grid = true, xAxis = nothing,
     figure = 1, prefix = "", reuse = false, maxLegend = 10,
     minXaxisTickLabels = false,
     MonteCarloAsArea = true)
```

Generate **line plots** of the signals of the `result` data structure that are identified with the `names` keys using the plot package defined with `ModiaResult.@usePlotPackage(xxx)`. Possible values for `xxx`: `"GLMakie", "WGLMakie", "CairoMakie", "PyPlot", "NoPlot", "SilentNoPlot"`).

`result` is any data structures that supports the abstract interface of `ModiaResult`.  Currently these are:

  * `result::ModiaResult.ResultDict`
  * `result::AbstractDict{String,T}`
  * `result::DataFrames.DataFrame`
  * `result` supports the `Tables.jl` interface with `Tables.columnaccess(result) = true`.

Argument `names` defines the diagrams to be drawn and the result data to be included in the respective diagram:

  * If `names` is a **String**, generate one diagram with one time series of the variable with key `names`.
  * If `names` is a **Tuple** of Strings, generate one diagram with the time series of the variables with the keys given in the tuple.
  * If names is a **Vector** or a **Matrix** of **Strings** and/or **Tuples**,  generate a vector or matrix of diagrams.

Note, the names (and their units, if available in the result) are automatically used as legends in the respective diagram.

A signal variable identified by a `String` key can be a scalar of type `<:Number` or an array of element type `<:Number`. A signal is defined by a vector of time values, a corresponding vector of signal values, and the signal type (continuous or clocked).

Note, before passing data to the plot package, it is converted to Float64. This allows to, for example, also plot rational numbers, even if not supported by the plot package. `Measurements.Measurement{xxx}`  and `MonteCarloMeasurements` is specially handled.

# Optional Arguments

  * `heading::AbstractString`: Optional heading above the diagram.
  * `grid::Bool`: = true, to display a grid.
  * `xAxis::Union{AbstractString,Nothing}`: Name of x-axis. If `xAxis=nothing`, the independent variable of the result (usually `"time"` is used as x-axis.
  * `figure::Int`: Integer identifier of the window in which the diagrams shall be drawn.
  * `prefix::AbstractString`: String that is appended in front of every legend label  (useful especially if `reuse=true`).
  * `reuse::Bool`: If figure already exists and reuse=false, clear the figure before adding the plot.  Otherwise, include the plot in the existing figure without removing the curves present in the figure.  `reuse = true` is ignored for `"WGLMakie"` (because not supported).
  * `maxLegend::Int`: If the number of legend entries in one plot command `> maxLegend`,  the legend is suppressed. All curves have still their names as labels. In PyPlot, the curves can be inspected by  their names by clicking in the toolbar of the plot on button `Edit axis, curve ..`  and then on `Curves`.
  * `minXaxisTickLabels::Bool`: = true, if xaxis tick labels shall be removed in a vector or array of plots, if not the last row (useful when including plots in a document). = false, x axis tick labels are always shown (useful when interactively zooming into a plot).
  * `MonteCarloAsArea::Bool`: = true, if MonteCarloMeasurements values are shown with the mean value and the area between the minimum and the maximum value of all particles. = false, if all particles of MonteCarloMeasurements values are shown (e.g. if a value has 2000 particles, then 2000 curves are shown in the diagram).

# Examples

```julia
import ModiaResult
using  Unitful

# Generate "using xxx" statement 
# (where "xxx" is from a previous ModiaResult.usePlotPackage("xxx"))
ModiaResult.@usingModiaPlot

# Construct result data
t = range(0.0, stop=10.0, length=100);
result = Dict{String,Any}();
result["time"] = t*u"s";
result["phi"]  = sin.(t)*u"rad";
result["w"]    = cos.(t)*u"rad/s";
result["a"]    = 1.2*sin.(t)*u"rad/s^2";
result["r"]    = hcat(0.4 * cos.(t), 0.5 * sin.(t), 0.3*cos.(t))*u"m";

# 1 signal in one diagram (legend = "phi [rad]")
plot(result, "phi")

# 3 signals in one diagram
plot(result, ("phi", "w", "a"), figure=2)

# 3 diagrams in form of a vector (every diagram has one signal)
plot(result, ["phi", "w", "r"], figure=3)

# 4 diagrams in form of a matrix (every diagram has one signal)
plot(result, ["phi" "w";
              "a"   "r[2]" ], figure=4)

# 2 diagrams in form of a vector
plot(result, [ ("phi", "w"), ("a") ], figure=5)

# 4 diagrams in form of a matrix
plot(result, [ ("phi",)           ("phi", "w");
               ("phi", "w", "a")  ("r[2:3]",)     ],figure=6)

# Plot w=f(phi) in one diagram
plot(result, "w", xAxis="phi", figure=7)

# Append signal of the next simulation run to figure=1
# (legend = "Sim 2: phi [rad]")
result["phi"] = 0.5*result["phi"];
plot(result, "phi", prefix="Sim 2: ", reuse=true)
```

Example of a matrix of plots:

![Matrix of plots](../resources/images/matrix-of-plots.png)
