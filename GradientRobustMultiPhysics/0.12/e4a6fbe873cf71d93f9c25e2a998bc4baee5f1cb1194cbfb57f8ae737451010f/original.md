```
function CombineDofs(idX::Int,idY::Int,dofsX::Array{Int,1},dofsY::Array{Int,1})
```

constructs a CombineDofs constraint that (if assigned to a PDEDescription) ensures that the dofsX of the unknown with id idX matches the dofsY of the unknown with id idY.
