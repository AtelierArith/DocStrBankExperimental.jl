```
bdplot_video(file::String, bd::Billiard, ps::Vector{<:AbstractParticle}; kwargs...)
```

Create an animation of `ps` evolving in `bd` and save it into `file`. This function shares all visualization-related keywords with [`bdplot_interactive`](@ref). Other keywords are:

  * `steps = 10`: How many `dt`-steps are taken between producing a new frame.
  * `frames = 1000`: How many frames to produce in total.
  * `framerate = 60`.
