```
Select
```

This structure acts a function when used within typical julia filtering functions,  by converting a string selection into a call to query call. 

# Example

Using a string to select the CA atoms of the first residue:

```jldoctest
julia> using PDBTools

julia> atoms = read_pdb(PDBTools.TESTPDB, "protein");

julia> findfirst(Select("name CA"), atoms)
5

julia> filter(Select("name CA and residue 1"), atoms)
   Vector{Atom{Nothing}} with 1 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       5   CA     ALA     A        1        1   -8.483  -14.912   -6.726  1.00  0.00     1    PROT         5

```
