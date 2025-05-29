```
load_particle_data(video_name::AbstractString)
```

Read a particle data `.csv` located in `/particle_data` into a `DataFrame`.

If the `.csv` file is from ImageJ (contains X, Y, and Label columns, not x, y, and frame), it will:

1. Extract the frame number from the label column and add it as a new column using [`extract_frame_from_label`](@ref)
2. Rename the `X` and `Y` columns to `x` and `y` so it works with [`link`](@ref).
3. Remove any columns with a blank name.
4. Rename the `Circ.` column to `Circ` so it works with Julia symbol notation.
