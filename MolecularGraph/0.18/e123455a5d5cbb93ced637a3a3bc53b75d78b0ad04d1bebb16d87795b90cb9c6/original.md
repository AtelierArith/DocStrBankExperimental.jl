```
nmap = emaptonmap(emap, mol, query)
```

Convert an edge-based mapping, of the form returned by [`edge_substruct_matches`](@ref), into a map between nodes. Commonly, `nmap[i]` is a length-1 vector `[j]`, where `i=>j` is the mapping from `nodeattr(query, i)` to `nodeattr(mol, j)`. In cases where the mapping is ambiguous, `nmap[i]` may be multivalued.
