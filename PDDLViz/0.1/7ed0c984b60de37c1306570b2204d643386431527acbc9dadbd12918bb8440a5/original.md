```
new_canvas(renderer::Renderer)
new_canvas(renderer::Renderer, figure::Figure)
new_canvas(renderer::Renderer, axis::Axis)
new_canvas(renderer::Renderer, gridpos::GridPosition)
```

Creates a new [`Canvas`](@ref) to be used by `renderer`. An existing `figure`, `axis`, or `gridpos` can be specified to use as the base for the new canvas.
