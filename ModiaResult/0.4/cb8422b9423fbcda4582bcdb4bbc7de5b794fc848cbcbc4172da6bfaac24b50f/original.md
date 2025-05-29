```
usePlotPackage(plotPackage::String)
```

Define the ModiaPlot package that shall be used by command `ModiaResult.@usingModiaPlot`. If a ModiaPlot package is already defined, save it on an internal stack (can be reactivated with `usePreviousPlotPackage()`.

Possible values for `plotPackage`:

  * `"GLMakie"`
  * `"WGLMakie"`
  * `"CairoMakie"`
  * `"PyPlot"`
  * `"NoPlot"`
  * `"SilentNoPlot"`

# Example

```julia
import ModiaResult

ModiaResult.usePlotPackage("GLMakie")

module MyTest
    ModiaResult.@usingModiaPlot

    t = range(0.0, stop=10.0, length=100)
    result = Dict{String,Any}("time" => t, "phi" => sin.(t))

    plot(result, "phi")  # use GLMakie for the rendering
end
```
