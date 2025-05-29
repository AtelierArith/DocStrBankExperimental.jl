```
read_pdb(pdbfile::String, selection::String)
read_pdb(pdbfile::String; only::Function = all)

read_pdb(pdbdata::IOBuffer, selection::String)
read_pdb(pdbdata::IOBuffer; only::Function = all)
```

Reads a PDB file and stores the data in a vector of type `Atom`. 

If a selection is provided, only the atoms matching the selection will be read.  For example, `resname ALA` will select all the atoms in the residue ALA.

If the `only` function keyword is provided, only the atoms for which `only(atom)` is true will be read.

### Examples

```jldoctest
julia> using PDBTools

julia> protein = read_pdb(PDBTools.TESTPDB)
   Vector{Atom{Nothing}} with 62026 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ALA     A        1        1   -9.229  -14.861   -5.481  0.00  0.00     1    PROT         1
       2  HT1     ALA     A        1        1  -10.048  -15.427   -5.569  0.00  0.00     1    PROT         2
⋮
   62025   H1    TIP3     C     9339    19638   13.218   -3.647  -34.453  1.00  0.00     1    WAT2     62025
   62026   H2    TIP3     C     9339    19638   12.618   -4.977  -34.303  1.00  0.00     1    WAT2     62026

julia> ALA = read_pdb(PDBTools.TESTPDB,"resname ALA")
   Vector{Atom{Nothing}} with 72 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ALA     A        1        1   -9.229  -14.861   -5.481  0.00  0.00     1    PROT         1
       2  HT1     ALA     A        1        1  -10.048  -15.427   -5.569  0.00  0.00     1    PROT         2
⋮
    1339    C     ALA     A       95       95   14.815   -3.057   -5.633  1.00  0.00     1    PROT      1339
    1340    O     ALA     A       95       95   14.862   -2.204   -6.518  1.00  0.00     1    PROT      1340

julia> ALA = read_pdb(PDBTools.TESTPDB, only = atom -> atom.resname == "ALA")
   Vector{Atom{Nothing}} with 72 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ALA     A        1        1   -9.229  -14.861   -5.481  0.00  0.00     1    PROT         1
       2  HT1     ALA     A        1        1  -10.048  -15.427   -5.569  0.00  0.00     1    PROT         2
⋮
    1339    C     ALA     A       95       95   14.815   -3.057   -5.633  1.00  0.00     1    PROT      1339
    1340    O     ALA     A       95       95   14.862   -2.204   -6.518  1.00  0.00     1    PROT      1340
```
