```
coordgen(mol::MolGraph) -> Tuple{Array{Int,1},Array{Int,1}}
```

Generate 2D coordinates by using Schrodinger's coordgenlibs.

This will returns a tuple of `coords` and `styles` arrays. `coords` is a size(n, 2) matrix where n is atom count, which stores 2D coordinates (x, y) of each atoms. `styles` is a size e vector of wedge notation of stereobond, where e is bond count.
