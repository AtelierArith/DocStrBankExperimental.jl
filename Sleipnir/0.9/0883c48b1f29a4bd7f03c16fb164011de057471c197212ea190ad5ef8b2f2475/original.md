```
plot_glacier_vid(
    plot_type::String,
    H::Vector{Matrix{Float64}},
    glacier::Glacier2D,
    simuparams::SimulationParameters,
    pathVideo::String;
    framerate::Int=24,
    baseTitle::String=""
)
```

Generate various types of videos for glacier data. For now only the evolution of the glacier ice thickness is supported. More types of visualizations will be added in the future. 

# Arguments

  * `plot_type`: Type of plot to generate. Options are:

      * "thickness": Heatmap of the glacier thickness.
  * `H`: A vector of matrices containing the ice thickness over time. This should be   replaced by a Results instance in the future once Results no longer depends on   an iceflow model.
  * `glacier`: A glacier instance.
  * `simuparams`: The simulation parameters.
  * `pathVideo`: Path of the mp4 file to generate.

# Optional Keyword Arguments

  * `framerate`: The framerate to use for the video generation.
  * `baseTitle`: The prefix to use in the title of the frames. In each frame it is   concatenated with the value of the year in the form " (t=XXXX)".
