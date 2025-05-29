```
@enumx MoleculeVariant begin
    None = 1
    Protein = 2
end
```

分子のバリアントを表す列挙型

# 例

```jldoctest
julia> prot = Protein(System())
Molecule{Float32}: (idx = 1, name = "")

julia> isprotein(prot)
true

julia> prot.variant == MoleculeVariant.Protein
true
```
