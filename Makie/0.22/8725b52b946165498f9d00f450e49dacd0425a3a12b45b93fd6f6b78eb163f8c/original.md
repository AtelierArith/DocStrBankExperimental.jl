```
Figure(; [figure_padding,] kwargs...)
```

Construct a `Figure` which allows to place `Block`s like [`Axis`](@ref), [`Colorbar`](@ref) and [`Legend`](@ref) inside. The outer padding of the figure (the distance of the content to the edges) can be set by passing either one number or a tuple of four numbers for left, right, bottom and top paddings via the `figure_padding` keyword.

All other keyword arguments such as `size` and `backgroundcolor` are forwarded to the [`Scene`](@ref) owned by the figure which acts as the container for all other visual objects.
