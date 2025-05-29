```
plot2d(pos::AbstractVector, seg::Vector{<:AbstractVector{<:Integer}}, reltime=0.0; kwargs...)
```

Display a 2D plot with user-defined segments connecting points.

# Arguments

  * `pos`: A vector of 3D positions `[[x1,y1,z1], [x2,y2,z2], ...]`.
  * `seg`: A vector of segment definitions `[[index1, index2], [index3, index4], ...]` where indices refer to positions in `pos`.
  * `reltime`: The relative time (default: `0.0`).
  * `zoom`: Whether to enable zooming (default: `true`).
  * `front`: Whether using a front view (default: `false`, which means side view).
  * `fig`: The name of the figure to display (default: `""`).
  * `figsize`: The size of the figure in inches (default: `(6.4, 4.8)`).
  * `dpi`: The resolution of the figure (default: `100`).
  * `dz_zoom`: The z-axis offset in zoom view (default: `1.5`).
  * `dz`: The z-axis offset in normal view (default: `-5.0`).
  * `dx`: The x-axis offset (default: `-16.0`).
  * `xlim`: The x-axis limits (default: `nothing`).
  * `ylim`: The y-axis limits (default: `nothing`) (for side view the z-axis).
  * `xy`: The x-y coordinates of the text (default: `nothing`) (for side view the z-axis).
