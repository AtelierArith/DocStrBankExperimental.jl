```
load_mmcif(fname::AbstractString, ::Type{T} = Float32) -> System{T}
```

Read a PDBx/mmCIF file.

!!! note
    Models are stored as frames, using the model number as `frame_id`.

