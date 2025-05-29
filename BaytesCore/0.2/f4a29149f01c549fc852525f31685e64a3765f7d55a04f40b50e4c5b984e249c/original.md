```julia
struct ResampleTune{R<:BaytesCore.ResamplingMethod}
```

Stores information about resampling steps.

# Fields

  * `method::BaytesCore.ResamplingMethod`: Method for resampling.
  * `update::BaytesCore.Updater`: Stores if last iteration was resampled.
