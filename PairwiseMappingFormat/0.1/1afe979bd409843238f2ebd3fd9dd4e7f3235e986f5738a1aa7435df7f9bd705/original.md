```
target_coverage(rec::Record) -> Float64
```

Compute the fraction of the target covered by the alignment.

# Examples

```jldoctest
julia> target_coverage(record)
0.044934629307437725
```

See also: [`query_coverage`](@ref), [`aln_identity`](@ref)
