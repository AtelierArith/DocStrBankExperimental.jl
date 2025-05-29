```
FileIO.load(file, ::Type{<:UnfoldModel}; generate_Xs=true)
```

Load UnfoldModel from a .jld2 file.

By default, the designmatrix is reconstructed. If it is not needed set `generate_Xs=false` which improves time-efficiency.
