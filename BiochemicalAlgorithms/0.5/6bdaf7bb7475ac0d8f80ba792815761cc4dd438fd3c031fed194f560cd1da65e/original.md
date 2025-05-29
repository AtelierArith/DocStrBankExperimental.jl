```
load_pubchem_json(fname::AbstractString, ::Type{T} = Float32) -> System{T}
```

Read a PubChem JSON file.

!!! note
    Conformers are stored as frames.

