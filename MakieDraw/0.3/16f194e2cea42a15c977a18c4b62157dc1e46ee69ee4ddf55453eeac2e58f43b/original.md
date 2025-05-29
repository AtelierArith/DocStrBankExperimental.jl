```
CanvasSelect <: AbstractCanvasSelect

CanvasSelect(figure; [layers])
```

A menu widget for selecting active canvases.

It will deactivate all non-selected canvases, and select the active one.

# Arguments

  * `figure::Union{Figure,GridPosition}` a Figure or `GridPosition`.

# Keywords

  * `layers`: A `Dict{Symbol,Orbservable{Bool}}` where the Symbols are   the names that will appear in the `Menu`, and the Observables are   the initial

# Example

```julia
using MakieDraw, GLMakie

layers = Dict(
    :paint=>paint_canvas.active,
    :point=>point_canvas.active,
    :line=>line_canvas.active,
    :poly=>poly_canvas.active,
)

fig = Figure()
cs = CanvasSelect(fig[2, 1]; layers)
```
