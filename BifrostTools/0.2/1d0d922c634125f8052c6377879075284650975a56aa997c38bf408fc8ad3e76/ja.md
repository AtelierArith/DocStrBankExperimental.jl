```
BifrostExperiment(
    expname::String="none",
    expdir::String=pwd()
    ;
    mesh_file=nothing
    )
```

あなたのBifrost実験のための構造体。

フィールド:

```mesh            ::BifrostMesh
    expname         ::String
    expdir          ::String
    snaps           ::Vector{Int64}
    snapsize        ::Tuple{Int64, Int64, Int64}
    num_snaps       ::Int64
    num_primary_vars::Int64
```
