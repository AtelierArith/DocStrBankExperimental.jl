```
findunconnnodes(fens::FENodeSet, fes::AbstractFESet)
```

Find nodes that are not connected to any finite element.

## Returns

`connected` = array is returned which is for the node k either true (node k is      connected), or false (node k is not connected).
