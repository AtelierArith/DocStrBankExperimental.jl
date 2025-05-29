```
wget(PDBid; selection; format="mmCIF")
```

Retrieves a PDB file from the protein data bank. Selections may be applied.

The optional format argument can be either "mmCIF" or "PDB". The default is "mmCIF". To download the data of large structures, it is recommended to use the "mmCIF" format.

### Example

```jldoctest
julia> using PDBTools

julia> protein = wget("1LBD","chain A")
   Vector{Atom{Nothing}} with 1870 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     SER     A      225        1   45.228   84.358   70.638  1.00 67.05     1                 1
       2   CA     SER     A      225        1   46.080   83.165   70.327  1.00 68.73     1                 2
⋮
    1869  CG2     THR     A      462      238  -27.063   71.965   49.222  1.00 78.62     1              1869
    1870  OXT     THR     A      462      238  -25.379   71.816   51.613  1.00 84.35     1              1870

```
