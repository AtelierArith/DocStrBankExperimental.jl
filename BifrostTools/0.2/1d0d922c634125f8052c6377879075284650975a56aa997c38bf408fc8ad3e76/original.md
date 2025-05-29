```
BifrostExperiment(
    expname::String="none",
    expdir::String=pwd()
    ;
    mesh_file=nothing
    )
```

A struct for your Bifrost-experiment.

Fields:

```mesh            ::BifrostMesh
    expname         ::String
    expdir          ::String
    snaps           ::Vector{Int64}
    snapsize        ::Tuple{Int64, Int64, Int64}
    num_snaps       ::Int64
    num_primary_vars::Int64
```

---
