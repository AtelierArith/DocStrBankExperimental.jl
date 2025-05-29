```
delta([::Type{ElT} = Float64, ][flux::QN = QN(), ]is)
delta([::Type{ElT} = Float64, ][flux::QN = QN(), ]is::Index...)
```

Make an ITensor with storage type `NDTensors.DiagBlockSparse` with uniform elements `one(ElT)`. The ITensor only has diagonal blocks consistent with the specified `flux`.

If the element type is not specified, it defaults to `Float64`. If theflux is not specified, it defaults to `QN()`.
