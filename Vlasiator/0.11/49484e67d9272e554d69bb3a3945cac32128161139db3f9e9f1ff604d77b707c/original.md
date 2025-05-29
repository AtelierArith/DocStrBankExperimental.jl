```
write_vlsv(filein, fileout, newvars::Vector{Tuple{Vector, String, VarInfo}};
   force=false)
```

Generate a new VLSV `fileout` based on `filein`, with `newvars` added. `force=true` overwrites the existing `fileout`.
