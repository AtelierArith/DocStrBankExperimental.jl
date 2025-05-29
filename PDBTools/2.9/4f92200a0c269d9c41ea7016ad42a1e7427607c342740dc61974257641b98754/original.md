```
Chain
```

Creates a Chain data structure. Chains must be consecutive in the `atoms` vector, and are identified by having the same `chain`, `segment`, and `model` fields.

The Chain structure carries the properties of the atoms it contains, but it does not copy the original vector of atoms. This means that any changes made in the Chain structure atoms, will overwrite the original vector of atoms. 

# Examples

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.CHAINSPDB);

julia> chains = collect(eachchain(ats))
4-element Vector{Chain}[
    Chain(A-48 atoms)
    Chain(B-48 atoms)
    Chain(A-48 atoms)
    Chain(D-45 atoms)
]

julia> chains[1]
 Chain A with 48 atoms.
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ASP     A        1        1  133.978  119.386  -23.646  1.00  0.00     1    ASYN         1
       2   CA     ASP     A        1        1  134.755  118.916  -22.497  1.00  0.00     1    ASYN         2
⋮
      47 HD23     LEU     A        3        3  130.568  111.868  -26.242  1.00  0.00     1    ASYN        47
      48    O     LEU     A        3        3  132.066  112.711  -21.739  1.00  0.00     1    ASYN        48

julia> mass(chains[1])
353.37881000000016 

julia> model(chains[4])
2

julia> segname(chains[2])
"ASYN"
```
