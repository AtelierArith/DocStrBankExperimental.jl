```
particle_data_to_linked_data(video_name::AbstractString, translation_dict::Dict, linking_settings::NamedTuple)
```

Process particle data into linked trajectory data while calculating instantaneous velocity and other salient data. Returns a `DataFrame` that can then be saved to `linked_data` using [`save_linked_data_with_metadata`](@ref).

A particle data csv corresponding to `video_name` must be present in the `particle_data` folder. The `translation_dict`` is a dictionary detailing the information contained in the filename. For full explanation,  see the MicroTracker docs (ref needed).
