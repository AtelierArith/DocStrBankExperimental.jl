```
saveFigure(figure, file; kwargs...)
```

Save figure on file. The file extension defines the image format (for example `*.png`).

| Plot package | Supported file extensions                                                                                                 |
|:------------ |:------------------------------------------------------------------------------------------------------------------------- |
| GLMakie      | png, jpg, bmp                                                                                                             |
| WGLMakie     | png                                                                                                                       |
| CairoMakie   | png, pdf, svg, eps                                                                                                        |
| PyPlot       | depends on [backend](https://matplotlib.org/stable/tutorials/introductory/usage.html) (png, pdf, jpg, tiff, svg, ps, eps) |
| NoPlot       | Call is ignored                                                                                                           |

# Keyword arguments

  * resolution: (width::Int, height::Int) of the scene in dimensionless  units (equivalent to px for GLMakie and WGLMakie).

# Example

```julia
import ModiaResult
ModiaResult.@usingModiaPlot
...

plot(..., figure=1)
plot(..., figure=2)

saveFigure(1, "plot.png")   # save in png-format
saveFigure(2, "plot.svg")   # save in svg-format
```
