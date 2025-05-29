```
render(
    renderables::AbstractVector;
    camera::Union{Nothing, Camera} = nothing,
    canvas_width::Int64 = (camera === nothing ? DEFAULT_CANVAS_WIDTH : canvas_width(camera)),
    canvas_height::Int64 = (camera === nothing ? DEFAULT_CANVAS_HEIGHT : canvas_height(camera)),
    surface::CairoSurface = CairoSVGSurface(IOBuffer(), canvas_width, canvas_height)
)
```

Draw all `renderables` to a `surface` of dimensions `canvas_width` x `canvas_height`. All renderables must implement the `add_renderable!` function which adds rendering instructions to the render model.

The provided `camera` should be updated using the  `update_camera!()` function before calling `render`. If no `camera` is provided, the render function will default to fitting all renderable objects to the canvas.
