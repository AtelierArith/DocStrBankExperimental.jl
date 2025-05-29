```
add_protein_residue!(resname::String, reference_residue::PDBTools.ProteinResidue)
```

Function to add a custom protein residue to the list of protein residues. The function will return the `ProteinResidue` object that was added. To remove all custom protein residues use `remove_custom_protein_residues!()`.

# Example

```jldoctest
julia> using PDBTools

julia> remove_custom_protein_residues!();

julia> add_protein_residue!("sA", PDBTools.protein_residues["ALA"])
PDBTools.ProteinResidue("sA", "ALA", "A", "Aliphatic", false, true, 71.037114, 71.0779, 0, true)

julia> isprotein(Atom(resname="sA"))
true

julia> remove_custom_protein_residues!(); # clean up
```

Here we repeteadly call `remove_custom_residues!()` to guarantee the proper execution of the test codes, without any custom residues in the list of protein residues.
