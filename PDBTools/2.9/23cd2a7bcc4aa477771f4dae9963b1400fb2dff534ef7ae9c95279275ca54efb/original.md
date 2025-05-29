```
Model
```

Model data structure. It carries the data of a model in a PDB file. Models must be consecutive in the `atoms` vector, and are identified by having the same `model` field.

The Model structure carries the properties of the model it contains, but it does not copy the original vector of atoms, only the model meta data and the reference to the original vector. Thus, changes in the model atoms will be reflected in the original vector of atoms.

### Example

In the example below, 8S8N is PDB entry with 11 models.

```jldoctest
julia> using PDBTools

julia> ats = wget("8S8N");

julia> models = collect(eachmodel(ats))
11-element Vector{Model}[
    1-(234 atoms))
    2-(234 atoms))
    ⋮
    10-(234 atoms))
    11-(234 atoms))
]

julia> models[1]
 Model 1 with 234 atoms.
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     DLE     A        2        1   -5.811   -0.380   -2.159  1.00  0.00     1                 1
       2   CA     DLE     A        2        1   -4.785   -0.493   -3.227  1.00  0.00     1                 2
⋮
     233  HT2   A1H5T     B      101       13   -5.695    5.959   -3.901  1.00  0.00     1               233
     234  HT1   A1H5T     B      101       13   -4.693    4.974   -2.743  1.00  0.00     1               234

```
