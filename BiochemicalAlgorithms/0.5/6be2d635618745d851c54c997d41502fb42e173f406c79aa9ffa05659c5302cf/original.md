```
load_pdb(fname::AbstractString, ::Type{T} = Float32) -> System{T}
```

Read a PDB file.

!!! note
    Models are stored as frames, using the model number as `frame_id`.

