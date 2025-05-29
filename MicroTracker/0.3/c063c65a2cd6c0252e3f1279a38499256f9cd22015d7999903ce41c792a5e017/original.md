```
animate_trajectory_analyzer(linked_data, collapsed_data, particle_unique, savepath, [framerange]; animation_speed_multiplier=1, size_variable="Major_um", annotationkwargs...)
```

Export an animation of the trajectory analyzer and save it to `savepath`.

# Arguments

  * `linked_data` : `AbstractDataFrame`, time-series linked data, as returned by [`load_linked_data`](@ref) or [`batch_particle_data_to_linked_data`](@ref).
  * `collapsed_data` : `AbstractDataFrame`, collapsed data with a row per microbot, as returned by [`collapse_data`](@ref).
  * `particle_unique` : `AbstractString`. The unique identifier of the microbot to be analyzed.
  * `savepath` : `AbstractString`. The path to save the animation to.
  * `framerange` : (Optional) `UnitRange{Int64}`. The range of frames to be displayed. If not provided, the entire trajectory is animated.
  * `animation_speed_multiplier` : (Optional) `Int`. The speed of the animation. Defaults to 1.
  * `size_variable` : (Optional) `AbstractString`, The column name of the size variable to be displayed. Defaults to `"Major_um"`.
  * `annotationkwargs` : (Optional) Keyword arguments passed to [`plotannotatedframe_single()`](@ref).

# Example

```julia-repl
julia> trajectory_analyzer(linked_data, collapsed_data, "5_13p5_61p35-2", "my_animation.mp4")
[ Info: Creating animation: Frame = 5
...
[ Info: Saved animation to ~/my_animation.mp4
```
