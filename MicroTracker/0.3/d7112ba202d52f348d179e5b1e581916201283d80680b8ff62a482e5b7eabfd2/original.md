```
batch_particle_data_to_linked_data(translation_dict::Dict, linking_settings::NamedTuple; save_to_csv=true)
```

Process all `.csv` files in `particle_data` into linked trajectory data and concatenate the results.

Returns a `DataFrame` containing all linked data for the entire experimental array. This is also saved to `linked_data`  using [`save_linked_data_with_metadata`](@ref) for record keeping and further analysis.

The `translation_dict` is a dictionary detailing the information contained in the filename. `linking_settings` contains the input parameters for the linking algorithm and microscope information. Only one of these arguments may contain the `FPS`.

For full explanation, see the MicroTracker [Linking](@ref) docs.
