```
add_info_columns_from_filename(particle_data::AbstractDataFrame, translation_dict::AbstractDict)
```

Extract experimental metadata from the `filename` column and create a new column for each in `particle_data`. Returns a new `DataFrame`.

Assumes the filename is separated by underscores and periods are denoted by `p`. The `translation_dict` details the filename format. For full explanation, see the MicroTracker docs: [Translation Dictionary](@ref).
