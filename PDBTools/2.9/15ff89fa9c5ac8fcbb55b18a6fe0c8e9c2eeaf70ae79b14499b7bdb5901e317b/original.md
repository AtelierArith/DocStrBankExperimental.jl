```
mass(s::Sequence)
```

Returns the mass of a sequence of amino acids, given a `Sequence` struct type.

# Examples

```julia-repl
julia> seq = ["Alanine", "Glutamic acid", "Glycine"];

julia> mass(Sequence(seq))
257.2432

julia> seq = "AEG";

julia> mass(Sequence(seq))
257.2432

julia> seq = ["ALA", "GLU", "GLY"];

julia> mass(Sequence(seq))
257.2432
```
