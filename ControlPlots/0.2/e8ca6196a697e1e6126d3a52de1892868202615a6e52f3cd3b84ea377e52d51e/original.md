```
plot2d(pos_matix::AbstractMatrix, reltime; zoom=true, front=false, segments=6, fig="", dz_zoom=1.5, 
       dz=-5.0, dx=-16.0, xlim=nothing, ylim=nothing, xy=nothing)
```

Display a video-like 2D particle system by calling `plot2d` in a loop.

# Arguments

  * `pos_matix`: a matrix of 3D coordinates
  * `reltime`: The relative time. When called the first time, set to `0.0`.
  * `zoom`: Whether to enable zooming (default: `false`).
  * `front`: Whether using a front view (default: `false`, which means side view).
  * `segments`: The number of tether segments (default: `6`).
  * `fig`: The name of the figure to display (default: `""`).
  * `dz_zoom`: The z-axis offset in zoom view (default: `1.5`).
  * `dz`: The z-axis offset in normal view (default: `-5.0`).
  * `dx`: The x-axis offset (default: `-16.0`).
  * `xlim`: The x-axis limits (default: `nothing`).
  * `ylim`: The y-axis limits (default: `nothing`) (for side view the z-axis).
  * `xy`: The x-y coordinates of the text (default: `nothing`) (for side view the z-axis).
