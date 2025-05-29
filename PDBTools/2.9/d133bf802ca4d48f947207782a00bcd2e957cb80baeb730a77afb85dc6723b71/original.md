```
remove_custom_protein_residues!()
```

Function to remove all custom protein residues from the list of protein residues.

# Example

```jldoctest
julia> using PDBTools

julia> remove_custom_protein_residues!(); # clean up

julia> add_protein_residue!("sA", PDBTools.protein_residues["ALA"])
PDBTools.ProteinResidue("sA", "ALA", "A", "Aliphatic", false, true, 71.037114, 71.0779, 0, true)

julia> isprotein(Atom(resname="sA"))
true

julia> remove_custom_protein_residues!();

julia> isprotein(Atom(resname="sA"))
false
```

Here we repeteadly call `remove_custom_residues!()` to guarantee the proper execution of the test codes, without any custom residues in the list of protein residues.
