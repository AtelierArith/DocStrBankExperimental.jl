```
showFigure(figure)
```

| Plot package | Effect                              |
|:------------ |:----------------------------------- |
| GLMakie      | Show `figure` in the single window. |
| WGLMakie     | Show `figure` in the single window. |
| CairoMakie   | Call is ignored                     |
| PyPlot       | Call is ignored                     |
| NoPlot       | Call is ignored                     |

# Example

```julia
import ModiaResult
ModiaResult.@usingModiaPlot
...
plot(..., figure=1)
plot(..., figure=2)
plot(..., figure=3)

showFigure(2)
showFigure(1)
```
