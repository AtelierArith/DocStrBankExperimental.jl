```
eeg_topoplot(data::Vector{<: Real}, labels::Vector{<: AbstractString})
```

Attributes:

  * `positions::Vector{<: Point} = Makie.automatic`: Can be calculated from label (channel) names. Currently, only 10/20 montage has default coordinates provided.
  * `labels::AbstractVector{<:AbstractString} = Makie.automatic`: Add custom labels, when `label_text` is set to true. If `positions` is not specified, `labels` are used to look up the 10/20 coordinates.
  * `head = (color=:black, linewidth=3)`: draw the outline of the head. Set to nothing to not draw the head outline, otherwise set to a namedtuple that get passed down to the `line!` call that draws the shape.

# Some attributes from topoplot are set to different defaults:

  * `label_scatter = true`
  * `contours = true`
  * `enlarge = 1``

Otherwise the recipe just uses the [`topoplot`](@ref) defaults and passes through the attributes.

!!! note
    The 10-05 channel locations are "perfect" spherical locations based on https://github.com/sappelhoff/eeg*positions/ - the mne-default 10-20 locations are _not*, they were warped to a fsaverage head. Which makes the locations provided here good for visualizations, but not good for source localisation.


!!! note
    You MUST set `label_text=true` for labels to display.

