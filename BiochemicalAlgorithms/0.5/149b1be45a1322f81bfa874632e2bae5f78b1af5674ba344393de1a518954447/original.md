```
@enumx MoleculeVariant begin
    None = 1
    Protein = 2
end
```

Enum representing variants of molecules

# Example

```jldoctest
julia> prot = Protein(System())
Molecule{Float32}: (idx = 1, name = "")

julia> isprotein(prot)
true

julia> prot.variant == MoleculeVariant.Protein
true
```
