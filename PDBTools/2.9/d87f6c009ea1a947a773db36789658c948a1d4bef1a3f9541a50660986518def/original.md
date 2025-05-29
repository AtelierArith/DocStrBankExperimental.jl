```
Atom::DataType
```

Structure that contains the atom properties. It is mutable, so its fields can be modified.

Fields:

```
mutable struct Atom{CustomType}
    index::Int32 # The sequential index of the atoms in the file
    index_pdb::Int32 # The index as written in the PDB file (might be anything)
    name::String7 # Atom name
    resname::String7 # Residue name
    chain::String3 # Chain identifier
    resnum::Int32 # Number of residue as written in PDB file
    residue::Int32 # Sequential residue (molecule) number in file
    x::Float32 # x coordinate
    y::Float32 # y coordinate
    z::Float32 # z coordinate
    beta::Float32 # temperature factor
    occup::Float32 # occupancy
    model::Int32 # model number
    segname::String7 # Segment name (cols 73:76)
    pdb_element::String3 # Element symbol string (cols 77:78)
    charge::Float32 # Charge (cols: 79:80)
    custom::CustomType # Custom fields
    flag::Int8 # Flag for internal use
end
```

### Example

```jldoctest
julia> using PDBTools

julia> atoms = read_pdb(PDBTools.SMALLPDB)
   Vector{Atom{Nothing}} with 35 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ALA     A        1        1   -9.229  -14.861   -5.481  0.00  0.00     1    PROT         1
       2 1HT1     ALA     A        1        1  -10.048  -15.427   -5.569  0.00  0.00     1    PROT         2
⋮
      34    C     ASP     A        3        3   -2.626  -10.480   -7.749  1.00  0.00     1    PROT        34
      35    O     ASP     A        3        3   -1.940  -10.014   -8.658  1.00  0.00     1    PROT        35

julia> resname(atoms[1])
"ALA"

julia> chain(atoms[1])
"A"

julia> element(atoms[1])
"N"

julia> mass(atoms[1])
14.0067

julia> position(atoms[1])
3-element StaticArraysCore.SVector{3, Float32} with indices SOneTo(3):
  -9.229
 -14.861
  -5.481
```

The `pdb_element` and `charge` fields, which are frequently left empty in PDB files, are not printed.  The direct access to the fields is considered part of the interface.

Custom fields can be set on `Atom` construction with the `custom` keyword argument. The Atom structure will then be parameterized with the type of `custom`. 

### Example

```jldoctest
julia> using PDBTools

julia> atom = Atom(index = 0; custom=Dict(:c => "c", :index => 1));

julia> typeof(atom)
Atom{Dict{Symbol, Any}}

julia> atom.custom
Dict{Symbol, Any} with 2 entries:
  :index => 1
  :c     => "c"

julia> atom.custom[:c]
"c"
```
