```
pdbentry(pdbid::AbstractString; format=MMCIFFormat, kws...)
```

Keyword arguments get propagated to [`BioStructures.downloadpdb`](https://biojulia.dev/BioStructures.jl/stable/api/#BioStructures.downloadpdb-Tuple{AbstractString})

Downloads are cached in a temporary directory.

## Examples

```jldoctest
julia> pdbentry("1EYE")
[ Info: Downloading file from PDB: 1EYE
1-element ProteinStructure "1EYE.cif":
 256-residue ProteinChain{Float64} (A)

julia> pdb"1EYE" # string macro for convenience
[ Info: File exists: 1EYE
1-element ProteinStructure "1EYE.cif":
 256-residue ProteinChain{Float64} (A)

julia> pdb"1EYE"A # string suffix to get a specific chain
[ Info: File exists: 1EYE
256-residue ProteinChain{Float64} (A)

julia> pdb"1EYE"1 # integer suffix to specify "ba_number" keyword
[ Info: Downloading file from PDB: 1EYE
2-element ProteinStructure "1EYE_ba1.cif":
 256-residue ProteinChain{Float64} (A)
 256-residue ProteinChain{Float64} (A-2)
```
