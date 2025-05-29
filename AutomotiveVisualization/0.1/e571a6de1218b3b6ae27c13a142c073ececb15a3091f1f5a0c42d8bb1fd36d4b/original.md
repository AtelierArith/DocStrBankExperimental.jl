```
RenderModel
```

Model to keep track of rendering instructions and background color.

  * `instruction_set::AbstractVector{Tuple}`: set of render instructions (function, array of inputs sans ctx, coordinate_system)
  * `background_color::RGB`: background color

## Fields

  * `instruction_set  :: AbstractVector{Tuple} = Array{Tuple}(undef, 0)`
  * `background_color :: RGB = colortheme["background"]`
