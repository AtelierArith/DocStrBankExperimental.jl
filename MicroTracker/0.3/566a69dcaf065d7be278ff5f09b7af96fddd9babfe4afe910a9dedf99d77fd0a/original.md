```
trajectory_analyzer(linked_data, collapsed_data, particle_unique::AbstractString, [framenumber; [size_variable="Major_um"], [annotationkwargs...])
```

Display a comphrehensive dashboard of a single microbot, including instantaneous velocity, a chosen `size_variable`, and the FFT of the `size_variable`.

# Arguments

  * `linked_data` : `AbstractDataFrame`, time-series linked data, as returned by [`load_linked_data`](@ref) or [`batch_particle_data_to_linked_data`](@ref).
  * `collapsed_data` : `AbstractDataFrame`, collapsed data with a row per microbot, as returned by [`collapse_data`](@ref).
  * `particle_unique` : `AbstractString`. The unique identifier of the microbot to be analyzed.
  * `framenumber` : (Optional) `Int` The frame number to be displayed. If not provided, the last frame is used.
  * `size_variable` : (Optional) `AbstractString`, The column name of the size variable to be displayed. Defaults to `"Major_um"`.
  * `annotationkwargs` : (Optional) Keyword arguments passed to [`plotannotatedframe_single()`](@ref).
