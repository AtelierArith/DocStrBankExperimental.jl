```
read_mmcif(mmCIF_file::String, selection::String; field_assignment)
read_mmcif(mmCIF_file::String; only::Function = all, field_assignment)

read_mmcif(mmCIF_data::IOBuffer, selection::String; field_assignment)
read_mmcif(mmCIF_data::IOBuffer; only::Function = all, field_assignment)
```

Reads a mmCIF file and stores the data in a vector of type `Atom`. 

All fields except the file name are optional.

If a selection is provided, only the atoms matching the selection will be read.  For example, `resname ALA` will select all the atoms in the residue ALA.

If the `only` function keyword is provided, only the atoms for which `only(atom)` is true will be returned.

The `field_assignment` keyword is `nothing` (default) or a `Dict{String,Symbol}` and can be used to specify which fields in the mmCIF file should be read into the `Atom` type. For example `field_assignment = Dict("type_symbol" => :name)` will read the `_atom_site.type_symbol` field in the mmCIF  file into the `name` field of the `Atom` type.

The default assignment is follows the standard mmCIF convention:

```julia
Dict{String,Symbol}(
    "id" => :index_pdb
    "Cartn_x" => :x
    "Cartn_y" => :y
    "Cartn_z" => :z
    "occupancy" => :occup
    "B_iso_or_equiv" => :beta
    "pdbx_formal_charge" => :charge
    "pdbx_PDB_model_num" => :model
    "label_atom_id" => :name
    "label_comp_id" => :resname
    "label_asym_id" => :chain
    "auth_seq_id" => :resnum
    "type_symbol" => :pdb_element
)
```

Source: https://mmcif.wwpdb.org/docs/tutorials/content/atomic-description.html

### Examples

```jldoctest
julia> using PDBTools

julia> ats = read_mmcif(PDBTools.TESTCIF)
   Vector{Atom{Nothing}} with 76 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     GLY     A        1        1   -4.564   25.503   24.113  1.00 24.33     1                 1
       2   CA     GLY     A        1        1   -4.990   26.813   24.706  1.00 24.29     1                 2
⋮
      75    O     HOH     Q       63       15   -3.585   34.725   20.903  1.00 19.82     1              2980
      76    O     HOH     Q       64       16   -4.799   40.689   37.419  1.00 20.13     1              2981

julia> ats = read_mmcif(PDBTools.TESTCIF, "index < 3")
   Vector{Atom{Nothing}} with 2 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     GLY     A        1        1   -4.564   25.503   24.113  1.00 24.33     1                 1
       2   CA     GLY     A        1        1   -4.990   26.813   24.706  1.00 24.29     1                 2

julia> ats = read_mmcif(PDBTools.TESTCIF; only = at -> name(at) == "CA")
   Vector{Atom{Nothing}} with 11 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       2   CA     GLY     A        1        1   -4.990   26.813   24.706  1.00 24.29     1                 2
       6   CA     GLN     A        2        2   -4.738   30.402   23.484  1.00 23.74     1                 6
⋮
      70   CA      CA     G     1003       10  -24.170   27.201   64.364  1.00 27.40     1              2967
      71   CA      CA     H     1004       11  -10.624   32.854   69.292  1.00 29.53     1              2968

```
