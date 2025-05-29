```
render_storyboard(anim::Animation, [idxs]; options...)
```

Renders an [`Animation`](@ref) as a series of (bitmap) images in a storyboard. Returns a `Figure` where each frame is a subplot.

The frames to render can be specified by `idxs`, a vector of indices. If `idxs` is not specified, all frames are rendered.

# Options

  * `n_rows = 1`: Number of storyboard rows.
  * `n_cols = nothing`: Number of storyboard columns (default: number of frames).
  * `figscale = 1`: Scales figure size relative to number of pixels required   to fit all frames at their full resolution.
  * `titles`: List or dictionary of frame titles.
  * `subtitles`: List or dictionary of frame subtitles.
  * `xlabels`: List or dictionary of x-axis labels per frame.
  * `ylabels`: List or dictionary of y-axis labels per frame.

Options that control title and label styling (e.g. `titlesize`) can also be specified as keyword arguments. See `Axis` for details.
