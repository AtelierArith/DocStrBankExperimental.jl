```
aln_identity(rec::Record) -> Float64
```

Return the nucleotide / residue identity, defined as the number of matches divided by the alignment length. This is a number between 0 and 1.

# Examples

```jldoctest
julia> aln_identity(record)
1.0
```

See also: [`query_coverage`](@ref), [`target_coverage`](@ref)
