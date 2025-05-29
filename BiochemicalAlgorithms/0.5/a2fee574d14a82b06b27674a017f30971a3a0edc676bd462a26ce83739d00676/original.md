```
@enumx FragmentVariant begin
    None = 1
    Residue = 2
    Nucleotide = 3
end
```

Enum representing variants of fragments

# Example

```jldoctest
julia> res = Residue(Chain(Molecule(System())), 1; name = "ALA")
Fragment{Float32}: (idx = 3, number = 1, name = "ALA")

julia> isresidue(res)
true

julia> res.variant == FragmentVariant.Residue
true
```
