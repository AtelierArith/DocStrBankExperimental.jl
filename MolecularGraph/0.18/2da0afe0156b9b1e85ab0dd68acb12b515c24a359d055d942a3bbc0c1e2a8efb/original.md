```
substruct_matches(mol1, mol2; kwargs...) -> Iterator
```

Return a lazy iterator that generate node mappings between `mol` and `query` if `mol` has `query` as a substructure.

# options

  * `vmatch::Function`: a function for semantic atom attribute matching (default: `MolecularGraph.vmatch`)
  * `ematch::Function`: a function for semantic bond attribute matching (default: `MolecularGraph.ematch`)
  * `mandatory::Dict{Int,Int}`: mandatory node mapping (or edge mapping if matchtype=:edgeinduced)
  * `forbidden::Dict{Int,Int}`: forbidden node mapping (or edge mapping if matchtype=:edgeinduced)
  * `timeout::Union{Int,Nothing}`: if specified, abort vf2 calculation when the time reached and return empty iterator (default: 10 seconds).
