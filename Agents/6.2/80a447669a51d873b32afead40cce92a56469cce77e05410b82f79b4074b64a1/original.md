```
abmvideo(file, model; kwargs...)
```

This function exports the animated time evolution of an agent based model into a video saved at given path `file`, by recording the behavior of the interactive version of [`abmplot`](@ref) (without sliders). The plotting is identical as in [`abmplot`](@ref) and applicable keywords are propagated.

## Keywords

  * `dt = 1`: Time to evolve between each recorded frame. For [`StandardABM`](@ref) this must be an integer and it is identical to how many steps to take per frame.
  * `framerate = 30`: The frame rate of the exported video.
  * `frames = 300`: How many frames to record in total, including the starting frame.
  * `title = ""`: The title of the figure.
  * `showstep = true`: If current step should be shown in title.
  * `figure = NamedTuple()`: Figure related keywords (e.g. resolution, backgroundcolor).
  * `axis = NamedTuple()`: Axis related keywords (e.g. aspect).
  * `recordkwargs = NamedTuple()`: Keyword arguments given to `Makie.record`. You can use `(compression = 1, profile = "high")` for a higher quality output, and prefer the `CairoMakie` backend. (compression 0 results in videos that are not playable by some software)
  * `kwargs...`: All other keywords are propagated to [`abmplot`](@ref).
