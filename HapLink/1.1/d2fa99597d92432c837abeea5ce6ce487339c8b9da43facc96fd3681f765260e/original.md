```
pseudoreads(sam::Union{AbstractString,AbstractPath}, consensus::NucleotideSeq)
```

Create a set of [`Pseudoread`](@ref)s from the alignments present in `sam` when aligned against `consensus`.
