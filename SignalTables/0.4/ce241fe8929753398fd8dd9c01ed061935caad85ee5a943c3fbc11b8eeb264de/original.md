```
usePlotPackage(plotPackage::String)
```

Define the plot package that shall be used by command `@usingPlotPackage`. If a PlotPackage package is already defined, save it on an internal stack (can be reactivated with `usePreviousPlotPackage()`.

Possible values for `plotPackage`:

  * `"PyPlot"`
  * `"GLMakie"`
  * `"WGLMakie"`
  * `"CairoMakie"`
  * `"SilentNoPlot"`

# Example

```julia
using SignalTables
usePlotPackage("GLMakie")

module MyTest
    using SignalTables
    @usingPlotPackage

    t = range(0.0, stop=10.0, length=100)
    result = Dict{String,Any}("time" => t, "phi" => sin.(t))

    plot(result, "phi")  # use GLMakie for the rendering
end
```
