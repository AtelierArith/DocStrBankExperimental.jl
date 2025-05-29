```
eachchain(atoms::AbstractVector{<:Atom})
```

Iterator for the chains of a selection. 

### Example

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.CHAINSPDB);

julia> eachchain(ats)
 Chain iterator with length = 4

julia> chains = collect(eachchain(ats))
4-element Vector{Chain}[
    Chain(A-48 atoms)
    Chain(B-48 atoms)
    Chain(A-48 atoms)
    Chain(D-45 atoms)
]
```
